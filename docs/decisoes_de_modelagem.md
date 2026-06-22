# Decisões de Modelagem

## Abordagem Geral

O projeto foi desenvolvido utilizando uma modelagem dimensional em formato **Star Schema**, separando a tabela fato das tabelas dimensão. Essa estrutura foi escolhida por facilitar a criação de relacionamentos, melhorar a organização do modelo semântico e permitir análises mais claras no Power BI.

A tabela fato concentra os registros principais dos testes de Hantavírus, enquanto as tabelas dimensão armazenam informações descritivas, como região, data, exposição, paciente e tipo de vírus.

---

## Modelo Dimensional

O modelo foi estruturado da seguinte forma:

- **Fact_Hantavirus**: tabela fato principal, contendo os registros dos testes, indicadores clínicos, severidade, resultado positivo/negativo e chaves de relacionamento.
- **Dim_Date**: dimensão de datas, criada a partir da coluna `Sample_Date`.
- **Dim_Region**: dimensão responsável pela segmentação regional.
- **Dim_Exposure**: dimensão com os tipos de exposição associados aos pacientes.
- **Dim_Patient**: dimensão com informações demográficas dos pacientes, como idade, faixa etária e gênero.
- **Dim_Virus**: dimensão contendo os tipos de Hantavírus identificados nos casos positivos.

---

## Justificativa do Star Schema

O Star Schema foi escolhido porque permite uma leitura mais simples do modelo e facilita a análise dos dados no dashboard. Como o projeto envolve diferentes perspectivas de análise — região, tempo, exposição, paciente e tipo de vírus — a separação em dimensões tornou o modelo mais organizado e adequado para consultas analíticas.

Essa estrutura também reduz a duplicidade de atributos descritivos na tabela fato e permite que os filtros aplicados nas dimensões afetem corretamente os indicadores calculados em DAX.

---

## Transformações em Power Query

Durante a etapa de transformação dos dados no Power Query, foram realizadas as seguintes decisões:

- Ajuste dos tipos de dados das colunas, como datas, textos e valores numéricos.
- Criação da coluna `Age_Group`, agrupando os pacientes por faixas etárias.
- Criação da dimensão de datas com colunas auxiliares como ano, mês, `YearMonth` e `YearMonthSort`.
- Remoção de duplicatas nas tabelas dimensão para garantir relacionamentos um-para-muitos.
- Criação de colunas de severidade clínica para facilitar a análise de indicadores como plaquetas, creatinina e BUN.
- Manutenção da tabela fato com os campos necessários para cálculo dos indicadores e relacionamento com as dimensões.

---

## Dimensão de Datas

A dimensão de datas foi criada para permitir análises temporais mais consistentes. Além da data original do exame, foram adicionadas colunas como:

- Ano;
- Mês;
- Nome do mês;
- YearMonth;
- YearMonthSort.

A coluna `YearMonthSort` foi criada para garantir que os meses fossem exibidos corretamente em ordem cronológica nos gráficos, evitando ordenação alfabética ou agrupamentos incorretos entre diferentes anos.

---

## Faixas Etárias

A coluna `Age_Group` foi criada para facilitar a análise demográfica dos pacientes. Em vez de analisar cada idade individualmente, os pacientes foram agrupados em categorias mais fáceis de interpretar em gráficos e filtros.

As faixas utilizadas foram:

- Crianças e adolescentes (menores de idade);
- Jovens adultos;
- Adultos;
- Idosos.

Essa decisão permitiu comparar grupos populacionais de forma mais clara na análise regional.

---

## Medidas em DAX

As principais métricas do projeto foram implementadas como medidas DAX. Foram criadas medidas para contagem de testes, casos positivos, casos graves, taxas percentuais, indicadores clínicos e metas dos KPIs.

Exemplos de medidas utilizadas:

- Total de Testes;
- Casos Positivos;
- Taxa de Positividade;
- Casos Graves;
- Taxa de Casos Graves;
- Taxa de Alto Risco Imunológico;
- Taxa de Plaquetas Severas;
- Taxa de Creatinina Severa;
- Taxa de Alto Risco Renal.

A utilização de medidas, em vez de colunas calculadas para todos os indicadores, permite que os valores respondam dinamicamente aos filtros aplicados no dashboard, como região, ano e tipo de exposição.

---

## Row-Level Security (RLS)

Foi implementado Row-Level Security com base na dimensão regional. A lógica criada permite simular diferentes perfis de acesso, em que cada gestor regional visualiza apenas os dados da sua respectiva região.

Exemplos de papéis criados:

- WHO_Global_Admin;
- WHO_AS_Manager;
- WHO_EU_Manager;
- WHO_NA_Manager;
- WHO_SA_Manager.

Essa decisão está alinhada ao cenário do projeto, no qual gestores regionais da OMS precisam acessar apenas os dados relacionados à sua área de atuação, enquanto usuários administrativos podem visualizar o conjunto completo dos dados.

---

## Drillthrough e Navegação

O dashboard utiliza drillthrough para permitir que o usuário parta da visão global e aprofunde a análise em uma região específica. Essa decisão foi tomada para criar uma experiência de investigação progressiva:

1. Visão global dos casos;
2. Investigação regional;
3. Avaliação clínica dos casos.

Dessa forma, o dashboard não funciona apenas como um conjunto de gráficos, mas como uma ferramenta de apoio à decisão, conduzindo o usuário da visão executiva até a análise clínica detalhada.

---

## Decisões de Visualização

As páginas do dashboard foram organizadas de acordo com diferentes níveis de análise:

- **Executive Monitoring Dashboard:** visão global para identificar regiões prioritárias.
- **Regional Risk Assessment:** análise dos fatores de exposição, perfil demográfico e risco regional.
- **Clinical Severity Assessment:** análise dos indicadores clínicos relacionados à severidade.

Essa divisão foi escolhida para evitar excesso de informações em uma única página e tornar a navegação mais intuitiva para diferentes perfis de usuários.