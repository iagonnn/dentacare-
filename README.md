# DentaCare — site estático

Site da clínica odontológica, exportado a partir do projeto Framer
(`dentacaredental.framer.website`) para HTML estático.

**O que é local:** HTML pré-renderizado, imagens, fontes e vídeos — tudo
hospedado neste repositório.

**O que vem do Framer (CDN):** apenas o runtime JavaScript (`framerusercontent.com`),
responsável pela hidratação, animações de entrada e interações (menu mobile, FAQ).
Tentar hospedar esse JS localmente quebra a hidratação do React (o runtime do
Framer usa `new URL()` com caminhos absolutos), então ele é mantido no CDN.

> ⚠️ Consequência: o JS continua dependendo do projeto seguir **publicado no
> Framer** (mesmo no plano grátis). Se o projeto for despublicado, as animações
> e interações param — o conteúdo (texto e imagens) continua aparecendo, pois é
> tudo SSR local. Para independência 100%, veja "Independência total" abaixo.

## Estrutura

```
index.html                      Home
about-us/index.html             Sobre
services/index.html             Serviços
blog/index.html                 Blog (listagem)
blog/<slug>/index.html          Posts do blog
contact-us/index.html           Contato
legal-pages/terms-conditions/   Termos
404.html                        Página de erro
assets/                         Imagens, fontes, vídeos e módulos JS (.mjs)
```

## Pré-visualizar localmente

Precisa de um servidor HTTP (os módulos ES não carregam via `file://`):

```bash
npx serve .
# ou
python -m http.server 8000
```

Depois abra http://localhost:8000

## Publicar no GitHub Pages

1. Suba este diretório para um repositório no GitHub.
2. Settings → Pages → Source: `Deploy from a branch` → branch `main`, pasta `/ (root)`.
3. O arquivo `.nojekyll` já está incluído para o GitHub servir todos os arquivos
   corretamente.

Para usar o domínio próprio (ex.: `dentalbrooklin.com.br`), adicione um arquivo
`CNAME` com o domínio e configure o DNS conforme a documentação do GitHub Pages.

## Independência total (opcional)

Hoje o JS depende do Framer. Para zerar essa dependência, as opções são:
1. Manter o projeto publicado no Framer (grátis funciona) — solução atual.
2. Plano pago do Framer com exportação de código.
3. Recriar a página em código limpo (HTML/CSS/JS próprio) usando este export
   como referência visual.

## Observações

- Os scripts de edição e o badge "Made in Framer" foram removidos.
- As meta tags `og:url` / `canonical` ainda apontam para o domínio antigo do
  Framer — atualize para o domínio final do cliente quando definido.
- O botão "Book A Call" aponta para um Calendly do criador do template original;
  troque pelo agendamento/contato da clínica.
