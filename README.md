# Ponto Q 🎀

App instalável (PWA) que calcula o ponto Q de um transistor NPN com polarização por divisor de tensão, com o passo a passo das análises aproximada e exata, o esquema com as tensões e a reta de carga.

Funciona sem internet depois de instalado.

## Conteúdo da pasta

| Arquivo | Para que serve |
|---|---|
| `index.html` | O app inteiro (HTML, CSS e JS num arquivo só) |
| `manifest.webmanifest` | Nome, cores e ícones que o celular usa ao instalar |
| `sw.js` | Service worker: guarda tudo no aparelho para funcionar offline |
| `icons/` | Ícones (normal, adaptável do Android e do iPhone) |
| `fonts/` | Fontes Fredoka e IBM Plex embutidas |

## 1. Publicar (GitHub Pages, de graça)

O celular só instala um PWA servido por **HTTPS**, então ele precisa estar hospedado.

1. Crie um repositório público no GitHub, por exemplo `ponto-q`.
2. Envie o conteúdo desta pasta para a raiz do repositório. Pode ser por **Add file → Upload files**, arrastando tudo, ou pelo terminal:
   ```bash
   git init && git add . && git commit -m "Ponto Q"
   git branch -M main
   git remote add origin git@github.com:SEU_USUARIO/ponto-q.git
   git push -u origin main
   ```
3. No repositório, abra **Settings → Pages**. Em *Build and deployment*, escolha **Deploy from a branch**, depois a branch `main` e a pasta `/ (root)`. Salve.
4. Em um ou dois minutos o app estará em `https://SEU_USUARIO.github.io/ponto-q/`.

Netlify, Vercel ou Cloudflare Pages também servem: é só apontar para esta pasta (é um site estático, sem build).

## 2. Instalar no celular

**Android (Chrome):** abra o link. Aparece o botão **Instalar app** no topo da página; se não aparecer, use o menu ⋮ e depois **Instalar app** (ou **Adicionar à tela inicial**).

**iPhone (Safari):** abra o link no Safari, toque em **Compartilhar** e depois em **Adicionar à Tela de Início**.

O ícone do Q com lacinho vai para a tela inicial e o app abre em tela cheia, sem barra do navegador.

## 3. Atualizar o app

Depois de mudar qualquer arquivo, troque a versão na primeira linha útil do `sw.js`:

```js
const CACHE = "ponto-q-v2";
```

Faça o push. Na próxima vez que o app abrir com internet, ele baixa a versão nova.

## Testar localmente

```bash
python3 -m http.server 8000
```

Depois abra `http://localhost:8000`. Em `localhost` o service worker funciona mesmo sem HTTPS.

## Quer na Play Store?

Com o app publicado, dá para gerar o pacote Android (`.aab`/`.apk`) a partir do link em [pwabuilder.com](https://www.pwabuilder.com). Ele empacota o PWA como app Android (Trusted Web Activity).
