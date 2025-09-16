# 🚲 Análise de Dados do Citi Bike NYC com BigQuery e Python

## 📌 Visão Geral
Este projeto tem como objetivo **extrair, tratar, explorar e analisar** dados públicos do sistema de bicicletas compartilhadas **Citi Bike** de Nova York, utilizando o **Google BigQuery** como fonte e **Python (Google Colab)** como ambiente de análise.

A análise busca responder perguntas de negócio relacionadas ao uso do sistema, como:
- Volume de viagens por período
- Padrões de uso por dia da semana e hora
- Estações mais movimentadas
- Diferenças de comportamento entre tipos de usuários
- Perfil etário e duração média das viagens

---

## 🛠 Tecnologias Utilizadas
- **Google BigQuery** – Consulta e extração de dados públicos
- **Google Colab** – Ambiente de desenvolvimento em Python
- **pandas** – Manipulação e tratamento de dados
- **pandas-gbq** – Integração Python ↔ BigQuery
- **matplotlib** e **seaborn** – Visualização de dados
- **NumPy** – Operações numéricas

---

## 📂 Fonte de Dados
- **Dataset:** `bigquery-public-data.new_york_citibike.citibike_trips`
- **Período disponível:** 2013-07-01 a 2018-05-31
- **Período analisado neste projeto:** Janeiro a Junho de 2017 (recorte para performance e foco)

---

## 🔍 Etapas do Projeto

### 1️⃣ Escolha e Diagnóstico da Base
- Consulta inicial ao BigQuery para identificar **intervalo de datas** e **volume total de registros**.
- Ajuste do período de análise para garantir dados disponíveis.

### 2️⃣ Extração dos Dados
- Uso da biblioteca `pandas-gbq` para rodar queries SQL diretamente no BigQuery.
- Seleção de colunas relevantes: datas, estações, tipo de usuário, duração e dados demográficos.

### 3️⃣ Tratamento dos Dados
- Conversão de colunas de data/hora para `datetime`.
- Criação de colunas derivadas:
  - `trip_min` (duração em minutos)
  - `month_trip` (mês/ano da viagem)
  - `dow` (dia da semana)
  - `hour` (hora do dia)
  - `age` e `age_band` (faixa etária)
- Remoção de outliers (viagens < 1 min ou > 180 min).
- Tratamento de valores ausentes e idades inválidas.

### 4️⃣ Análise Exploratória
- Estatísticas descritivas (`describe`, `value_counts`).
- Contagem e agrupamento por variáveis de interesse.
- Visualizações para identificar padrões.

### 5️⃣ Perguntas de Negócio Respondidas
1. **Volume por mês** – Quantidade de viagens mês a mês.
2. **Padrão por dia da semana e hora** – Heatmap de uso.
3. **Top 10 estações de partida e chegada** – Identificação de hubs.
4. **Duração por tipo de usuário** – Boxplot comparativo.
5. **Diferença entre dias úteis e fins de semana** – Comparação de demanda por hora.

---

## 📊 Principais Resultados

- **Picos de uso** nos horários de deslocamento (8–9h e 17–19h) em dias úteis.
- **Fins de semana** com uso mais distribuído ao longo do dia.
- **Estações mais movimentadas** localizadas próximas a hubs de transporte e áreas turísticas.
- **Assinantes** tendem a viagens mais curtas e regulares; **usuários ocasionais** apresentam maior variação de duração.
- Faixas etárias **25–44 anos** concentram a maior parte das viagens.

---

## 🚀 Como Executar
1. Abrir o [Google Colab](https://colab.research.google.com/).
2. Instalar dependências:
   ```python
   !pip install pandas-gbq google-auth --quiet
3. Autenticar no Google Cloud:
 from google.colab import auth
auth.authenticate_user()
4. Definir seu PROJECT_ID do GCP
5. Rodar a query de extração e seguir as etapas de tratamento e análise.

