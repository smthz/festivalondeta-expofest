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

## Adicionar um patrocinador

1. Salve a logo em `assets/img/patrocinadores/` — 360×200 px, com a arte já centralizada
   sobre o fundo que ela vai usar no card.
2. No `index.html`, procure por `s-nome-da-marca` no `<style>` e acrescente a regra da
   nova marca junto das outras:

```css
.s-nome-da-marca{background-color:#FFFFFF;background-image:url("assets/img/patrocinadores/nome-da-marca.png")}
```

   O `background-color` deve ser a mesma cor de fundo da logo — é ele que faz o card
   "sumir" atrás da arte.
3. Procure por `============ PATROCINADORES ============` e acrescente o item na lista:

```html
<li class="slot s-nome-da-marca" role="img" aria-label="Nome da Marca"></li>
```

4. **Acrescente o mesmo item nas duas listas.** A segunda (`aria-hidden="true"`) é a
   cópia técnica que faz a rolagem emendar sem salto; se as duas não forem iguais, a
   animação dá um pulo. Ela não aparece para leitores de tela nem em telas com
   movimento reduzido.
5. Atualize o número em `marcas confirmadas`, logo abaixo da faixa.
6. Intercale claro e escuro na ordem da lista — inclusive entre o último e o primeiro,
   que ficam lado a lado quando a rolagem emenda. Se a faixa passar de ~16 marcas,
   aumente o `57s` do `.mtrack` para a rolagem não ficar corrida.

## Manutenção

- Preços, cotas e prazos estão escritos direto no `index.html`, em português, fáceis de achar.
- Os esquemas dos cinco banners são SVG inline — dá para mexer em medidas e cores no código.
- Para trocar o vídeo, substitua `assets/video/festival.mp4` e a imagem
  `assets/video/festival-poster.jpg`, mantendo os nomes.
