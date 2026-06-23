# Dashboard de Monitoramento Global do Hantavírus

Projeto final para a aula Business Intelligence II desenvolvido em **Power BI** com o objetivo de apoiar o monitoramento e a análise de casos de Hantavírus por meio de dashboards interativos.

---

## Descrição do Projeto

Neste projeto, assumimos o papel de um time de Business Intelligence da **Organização Mundial da Saúde (OMS)**. Utilizando dados epidemiológicos e clínicos, foi desenvolvido um dashboard interativo para apoiar a identificação de regiões prioritárias, analisar fatores de exposição e avaliar indicadores clínicos relacionados à gravidade da doença.

O dashboard é composto por três páginas:

- **Monitoramento Global** – Visão executiva dos principais indicadores e regiões prioritárias.
- **Análise de Risco Regional** – Investigação dos fatores de exposição, perfil demográfico e distribuição dos casos por região.
- **Avaliação de Severidade Clínica** – Análise dos principais indicadores clínicos relacionados aos casos graves.

---

## Dataset

**Link:** https://www.kaggle.com/datasets/tousifahamedrahat12/hantavirus-detection-dataset

---

## Problema de Negócio

O objetivo deste projeto é apoiar a Organização Mundial da Saúde (OMS) na identificação das regiões com maior risco de ocorrência de Hantavírus, compreender os principais fatores associados aos casos positivos e graves e fornecer informações que auxiliem na tomada de decisões estratégicas para prevenção, monitoramento e alocação de recursos.

---

## Principais KPIs

- Total de Testes
- Casos Positivos
- Taxa de Positividade
- Casos Graves
- Taxa de Casos Graves
- Casos de Alto Risco Imunológico
- Taxa de Plaquetas Severas
- Taxa de Creatinina Severa
- Taxa de Alto Risco Renal

---

## Estrutura do Repositório

```text
docs/
├── problema_de_negocio.md
├── kpis_okrs.md
├── modelo_dimensional.png
└── decisoes_de_modelagem.md
data/
└── README.md
├── hantavirus_detection_dataset.csv
pbip/
└── Arquivos do projeto Power BI
apresentacao/
└── Apresentação_Hantavirus.pdf
```

---

## Como Executar o Projeto

1. Clone ou faça o download deste repositório.
2. Abra a pasta **pbip**.
3. Abra o arquivo **.pbip** utilizando o **Power BI Desktop**.
4. Caso necessário, atualize a fonte de dados.

---

## Tecnologias Utilizadas

- Power BI Desktop
- Power Query
- DAX
- Modelagem Dimensional (Star Schema)

---

Observação: Embora o dataset apresente algumas distribuições bastante equilibradas entre categorias, todas as análises e visualizações foram desenvolvidas com base nos dados disponibilizados, respeitando integralmente sua estrutura e características.

---

## Autores

- Gabriel Arakaki-Sanchez
- Vinicius Nogueira
