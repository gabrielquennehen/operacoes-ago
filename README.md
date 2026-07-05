# Dashboard — Planos de Ação de Desvios (Ageodonto)

Painel HTML estático que lê as planilhas dos consultores (Google Sheets) e consolida
resumo + drill-down por praça, com histórico, tendência e ações para o SULS.

## Estrutura
- `index.html` — o dashboard (arquivo único, sem build).
- `vercel.json` — configuração mínima (serve estático + cache do HTML sempre fresco).

## Subir no Vercel com URL fixa (recomendado)

1. Crie um repositório no GitHub (ex.: `ago-dashboard-desvios`) e envie estes arquivos:
   ```bash
   git init
   git add .
   git commit -m "Dashboard de desvios"
   git branch -M main
   git remote add origin https://github.com/SEU_USUARIO/ago-dashboard-desvios.git
   git push -u origin main
   ```
2. No Vercel: **Add New → Project → Import** o repositório.
3. Em Framework Preset deixe **Other**; Build Command **vazio**; Output Directory **. (ponto)**.
4. **Deploy**. A partir daí, todo `git push` atualiza o site sozinho, mantendo a MESMA URL.

## Abrir já conectado às planilhas (opcional, recomendado para URL compartilhada)

A conexão fica salva por navegador (localStorage). Para que o painel abra JÁ conectado
em qualquer dispositivo (Thaís, Dr. Carlos), fixe os links das 4 planilhas no código:

Em `index.html`, localize a linha:
```js
const SHEETS_HARDCODED = [];
```
e preencha com os links (planilhas como "qualquer pessoa com o link pode ver"):
```js
const SHEETS_HARDCODED = [
  "https://docs.google.com/spreadsheets/d/ID_PATRICK/edit",
  "https://docs.google.com/spreadsheets/d/ID_MARCELO/edit",
  "https://docs.google.com/spreadsheets/d/ID_CAMILA/edit",
  "https://docs.google.com/spreadsheets/d/ID_LILIAN/edit"
];
```
Faça `git push` e o painel passa a abrir consolidado para todos.

## Privacidade
A URL do Vercel é pública — trate como link interno (compartilhe só com Thaís e Dr. Carlos).
Para travar de verdade, use a Deployment Protection (proteção por senha) do Vercel.
