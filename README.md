# Festival Onde Tá? & ExpoFest — site de patrocínio

Página única, estática, sem build e sem dependências. É só HTML, CSS e um script pequeno.

## Estrutura

```
index.html                       página inteira (HTML + CSS + JS inline)
assets/img/                      marca, logos e imagens do projeto 3D
assets/fonts/                    Oswald e Public Sans (woff2, self-hosted)
assets/video/festival.mp4        passeio em 3D, 720p, ~12 MB
vercel.json                      cache dos assets
```

## Subir no GitHub

```bash
git init
git add .
git commit -m "Site de patrocínio do Festival Onde Tá? & ExpoFest"
git branch -M main
git remote add origin git@github.com:SEU-USUARIO/SEU-REPO.git
git push -u origin main
```

## Publicar na Vercel

1. Em vercel.com, **Add New → Project** e importe o repositório.
2. Framework Preset: **Other**. Não preencha build command nem output directory —
   é um site estático e a Vercel serve a raiz.
3. Deploy.

## Depois do primeiro deploy

Troque `SEU-DOMINIO.vercel.app` pelo domínio real em três lugares do `index.html`
(`link rel="canonical"`, `og:url`, `og:image` e `twitter:image`). Sem isso, a prévia
do link no WhatsApp não mostra a imagem de capa.

## Rodar localmente

```bash
python3 -m http.server 8000
# abre http://localhost:8000
```

## Manutenção

- Preços, cotas e prazos estão escritos direto no `index.html`, em português, fáceis de achar.
- Os esquemas dos cinco banners são SVG inline — dá para mexer em medidas e cores no código.
- Para trocar o vídeo, substitua `assets/video/festival.mp4` e a imagem
  `assets/video/festival-poster.jpg`, mantendo os nomes.
