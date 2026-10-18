# Finanças Unificado — Fluxo + Carteira

App financeiro pessoal: fluxo de caixa operacional (contas, provisionado, orçamentos, metas)
+ carteira analítica (7 classes, gráficos, Visão 360). Persistência local (kv + localStorage),
importação JSON/CSV/XLSX/OFX, cotações B3 e cripto.

## Estrutura

- `index.html` — UI completa (sidebar + 9 módulos + modais). É o conteúdo do `<body>` no Perchance;
  para GitHub Pages, embrulhe com `<html>/<head>/<body>` ou use o `index-standalone.html` do pacote.
- `main.pjs` — metadados + imports (`kv-plugin`, `super-fetch-plugin`, `upload-plugin`) + config.

## Módulos

- `inv` — Carteira de Investimentos (7 KPIs, 4 gráficos, tabela por classe)
- `fc` — Fluxo de Caixa (5 KPIs, 2 gráficos, lançamentos, provisionados)
- `360` — Visão 360° (5 KPIs, evolução mensal)
- `report` — Relatório Mensal por competência (6 blocos, impressão centralizada via `@media print`)
- `budget` — Orçamentos (teto por categoria)
- `goals` — Metas e Cofrinhos
- `accs` — Contas (saldo de lançamentos realizados)
- `sync` — Sincronização XLSX/OFX + nuvem multi-dispositivo
- `export` — Backup JSON, CSVs, atalho para o Relatório

## Rodar local

Sem build. Sirva a pasta por HTTP (ex: `npx serve .`) e abra no navegador.
Chart.js e XLSX vêm de CDN (jsdelivr). Persistência usa IndexedDB (kv-plugin no Perchance;
fora dele, o app usa localStorage — ver `saveUnified`/`loadUnified` em `index.html`).

## Publicar no GitHub Pages

1. Crie o repositório e suba `index.html` + `main.pjs` + este README.
2. Settings → Pages → Deploy from branch → `main` / root.
3. A URL sai como `https://<user>.github.io/<repo>/`.

## Backup

Exportar → Backup completo (JSON). É o único que sobrevive à limpeza dos dados do site.
