# DentaCare — site estático

Site da clínica odontológica, exportado a partir do projeto Framer
(`dentacaredental.framer.website`) para código estático **self-contained**:
HTML pré-renderizado + todos os assets (imagens, fontes, vídeos e JS) hospedados
localmente. Não depende mais do Framer para funcionar.

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

## Observações

- Os scripts de edição e o badge "Made in Framer" foram removidos.
- As meta tags `og:url` / `canonical` ainda apontam para o domínio antigo do
  Framer — atualize para o domínio final do cliente quando definido.
- O botão "Book A Call" aponta para um Calendly do criador do template original;
  troque pelo agendamento/contato da clínica.
