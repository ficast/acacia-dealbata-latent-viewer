# Acácia nos espaços latentes

Ferramenta de visual analytics da dissertação *Interpretable Latent Space Analysis for Forest Species using Satellite Images* (MIACD, Universidade de Coimbra).

Mostra como a *Acacia dealbata* e as classes de floresta e matos da COSc 2023 (eucalipto, outras folhosas, pinheiro-bravo, matos) se organizam nos espaços latentes de três *foundation models* de píxel (GeoTessera, AlphaEarth, Presto), no tile Sentinel-2 29TNE. As classes vêm de uma superfície COS + acácia: o mapa de acácia de 2023 feito na dissertação posto por cima das quatro classes da COS. É uma cópia de [cosc-latent-viewer](https://github.com/ficast/cosc-latent-viewer), que mostra só as classes da COS.

A acácia é uma amostra de toda a acácia do mapa (sem filtro de pureza); as classes da COS são píxeis puros. A página tem:

- projeções UMAP e t-SNE ligadas a um mapa com o OrtoSat 2023 da DGT e o Sentinel-2 cloudless 2023 da EOX;
- pureza e confusão dos vizinhos mais próximos, calculadas no espaço original de cada modelo.

## Estrutura

Site estático, sem build:

| Ficheiro | Conteúdo |
|---|---|
| `index.html`, `style.css`, `app.js` | A página (Leaflet 1.9.4 via unpkg) |
| `data.json` | Píxeis, projeções e métricas, gerado pelo notebook 49 do workspace da tese (`project/notebooks/experimentos_7/49_acacia_pixel_latent.ipynb`, exportado para `project/data/interim/acacia_final/latent/data.json`) |

## Correr localmente

```
python -m http.server 8765
```

e abrir http://127.0.0.1:8765/ (o `fetch` do `data.json` não funciona a partir de `file://`).

## Deploy

Vercel, como site estático (sem *framework*, sem comando de build, diretório de saída a raiz).

## Créditos das imagens

- OrtoSat 2023 © Direção-Geral do Território (WMS `ortos.dgterritorio.gov.pt/wms/ortosat2023`).
- Sentinel-2 cloudless 2023 — https://s2maps.eu by EOX IT Services GmbH (contém dados Copernicus Sentinel modificados de 2023), CC BY-NC-SA 4.0.
