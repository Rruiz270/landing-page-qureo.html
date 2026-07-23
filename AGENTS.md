# landing-page-qureo.html

Landing page estática da inscrição do **Campeonato QUREO 2025 Brasil** (formação de talentos em TIC / SPRIX Brasil), com hero, timeline e modal de inscrição.

## Stack
- **Linguagem:** HTML + CSS + JavaScript vanilla. Sem framework, sem build, sem banco.
- **Assets externos:** Google Fonts (DM Sans, Lexend) e logo `sprixbrasil.com.br/logo.svg` carregados via `<link>`/`<img>`.
- **Deploy:** hospedagem estática (servir os 3 arquivos). Sem `vercel.json`/`netlify.toml` no repo.
- **Package manager:** nenhum (não há `package.json` nem lockfile).

## Comandos
Não há toolchain. Fluxo real:
- **Pré-visualizar:** abrir `index.html` no navegador, ou `python3 -m http.server` na raiz e acessar `http://localhost:8000`.
- **Build / test / lint:** não existem.

## Estrutura
- `index.html` (~222 linhas) — página única: header, hero, timeline, modal de inscrição (`#registrationModal`, form `#registrationForm`).
- `styles.css` (~552 linhas) — todo o estilo.
- `script.js` (~106 linhas) — `openModal()`/`closeModal()`, submit do form, smooth scroll e animação da timeline via IntersectionObserver.
- `QUREO_Championship_Brazil_2025_PO (2).pdf` — material de referência do campeonato.

## Convenções de código
- HTML/CSS/JS separados em três arquivos (não inline). Mantenha esse padrão.
- Idioma pt-BR (`<html lang="pt-BR">`), textos em português.
- IDs em camelCase (`registrationForm`, `studentName`); classes CSS em kebab-case (`cta-button`, `hero-content`).
- Sem transpilação: use apenas JS que rode direto no navegador.

## Variáveis de ambiente
Nenhuma. Não há backend nem segredos no repo.

## CI/CD & Deploy
- Sem CI e sem config de deploy versionada; publicação é upload dos arquivos estáticos.
- **CI mínimo recomendado (em PR):** um linter de HTML (ex.: html-validate) e checagem de links quebrados; opcionalmente um `prettier --check`.

## Boas práticas de PR
- Branches: `feat/…`, `fix/…`, `chore/…`.
- Conventional Commits (`feat:`, `fix:`, `docs:`, `chore:`).
- PRs pequenos. Checklist:
  - [ ] Página abre sem erro no console; modal abre/fecha e o form reseta.
  - [ ] Nenhum segredo/token embutido.
  - [ ] Screenshot antes/depois de mudanças visuais (desktop + mobile).
- ≥1 review, squash merge, `main` sempre publicável.

## Testes
Não há testes. Verificação manual: abrir a página, testar o modal de inscrição, o submit e a responsividade (mobile/desktop). Recomendação mínima: um teste de smoke com Playwright validando abertura do modal e envio do form, se a página crescer.

## Segurança & dados
- **O form hoje não envia dados a lugar nenhum** — apenas `console.log` + `alert()` de sucesso (`script.js`). Ao ligar um backend, colete o mínimo, use HTTPS e trate dados de menores de idade (nome, escola, série, idade) sob **LGPD** com consentimento do responsável.
- Nunca commitar chaves/endpoints privados no JS do cliente.
- Assets de terceiros (fonts, logo SPRIX) vêm de domínios externos — considere hospedar localmente para evitar dependência/quebra.

## Gotchas
- O envio de inscrição é **fake**: só loga no console e mostra `alert`. Integrar um endpoint real é o próximo passo óbvio.
- Logo depende de `sprixbrasil.com.br/logo.svg`; se o domínio cair, o header quebra.
- Nome do repo termina em `.html` mas é um projeto (pasta), não um arquivo — não confundir.
- Sem etapa de build: edite os arquivos e publique como estão.
