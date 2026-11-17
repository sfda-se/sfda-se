# Mapa de Projetos do MDA em Sergipe

Mapa interativo dos projetos financiados pelo Ministério do Desenvolvimento Agrário e Agricultura Familiar (MDA) em Sergipe, elaborado pela Superintendência Federal de Desenvolvimento Agrário de Sergipe (SFDA-SE).

Ao clicar em um município, abre-se uma caixa de diálogo com os projetos do MDA naquela localidade: edital, proponente, instrumento, objeto, público-alvo, beneficiários e informações específicas do município, como documentos emitidos nos mutirões e cestas de alimentos distribuídas. O campo de busca na lateral localiza um município pelo nome.

## Estrutura

```
index.html                         página principal
css/style.css                      estilos
js/app.js                          lógica do mapa (Leaflet), busca e caixa de diálogo
data/municipios-geojson.js         malha municipal de Sergipe (IBGE 2025, simplificada)
data/projetos.js                   projetos por município e centroides (usado pelo mapa)
data/projetos-por-municipio.json   os mesmos projetos em JSON legível
.github/workflows/pages.yml        publicação automática no GitHub Pages
```

## Executar localmente

Não há dependências para instalar. Abra o `index.html` no navegador ou, se preferir, use um servidor local:

```
python3 -m http.server 8000
```

Depois acesse http://localhost:8000.

## Publicar no GitHub Pages

1. Crie um repositório no GitHub e envie estes arquivos para a branch `main`.
2. Em **Settings > Pages**, em **Build and deployment**, escolha **Source: GitHub Actions**.
3. A cada `push` na `main`, o workflow publica o site em `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/`.

## Atualizar os dados

Os dados exibidos no mapa estão em `data/projetos.js`, na estrutura `municipios > NOME DO MUNICÍPIO > lista de projetos`. Os nomes dos municípios devem ser idênticos aos da malha (campo `NM_MUN`), por exemplo "Graccho Cardoso" e "Itaporanga d'Ajuda". Cada projeto aceita os campos `nome`, `edital`, `processo`, `instrumento`, `proponente`, `objeto`, `publico_alvo`, `resultados`, `beneficiarios_se`, `equipamentos`, `beneficiarios_nome`, `valor` e `nota_local` (texto destacado como "Neste município"). A lista `centroids` guarda latitude e longitude do marcador de cada município.

## Fontes e tecnologias

- Malha municipal: IBGE, Municípios de Sergipe 2025.
- Projetos: planilha de levantamento da SFDA-SE.
- Mapa: [Leaflet](https://leafletjs.com/).
