# 📊 Dashboard de Criptomoedas – Power BI + BigQuery

## 📝 Descrição
Este projeto consiste na construção de um **dashboard interativo no Power BI**, utilizando dados de criptomoedas armazenados no **Google BigQuery**, com análises de **preços históricos** e **informações de mercado**.  
O objetivo é permitir uma visão clara da **evolução** e **comparação** entre as principais criptomoedas ao longo do tempo.

---

## 🔧 Tecnologias e Ferramentas

- **Google BigQuery**: Armazenamento e consulta dos dados (camada gratuita usada)  
- **Power BI**: Visualização e modelagem dos dados  
- **Power Query (M)**: Limpeza e transformação dos dados  
- **DAX**: Criação de medidas e cálculos personalizados  

---

## 📁 Estrutura dos Dados

### 📄 Tabela 1: `cryptocurrencies`

| Coluna            | Descrição                              |
|-------------------|----------------------------------------|
| `id`              | Identificador da criptomoeda           |
| `name`            | Nome da criptomoeda                    |
| `symbol`          | Símbolo (ex: BTC, ETH)                |
| `market_cap_rank` | Ranking por capitalização             |
| `current_price`   | Preço atual da moeda                  |

### 📄 Tabela 2: `price_history`

| Coluna        | Descrição                                                  |
|---------------|------------------------------------------------------------|
| `crypto_id`   | Referência ao ID da criptomoeda                            |
| `price_date`  | Data da cotação                                            |
| `price_usd`   | Preço da criptomoeda em USD na data                        |

---

## 📊 Visualizações no Dashboard

### 🔢 Cartões (KPIs):
- Criptomoeda mais cara  
- Criptomoeda com menor valor  
- Média de preço do Bitcoin  

### 📈 Gráfico de Linhas:
- Evolução de preço ao longo do tempo por moeda  

### 📉 Gráfico de Área Empilhada:
- Comparação entre múltiplas criptos com base em seus preços  

### 📋 Tabela:
- Visão geral com nome, símbolo, posição e preço atual  

### 📊 Gráfico de Barras:
- Ranking por capitalização de mercado  

---

## 🎛️ Funcionalidades Especiais

### 🔍 Filtros e Segmentações:
- Segmentação por nome da criptomoeda

### 🧮 Medidas Personalizadas com DAX:

media_XRP = 
CALCULATE(
    AVERAGE('price_history'[price_usd]), 
    'cryptocurrencies'[name] = "XRP"
)

## 🧼 Formatação de Valores:
Preços são exibidos com:
Duas casas decimais
Sufixo "k" para valores maiores que 1000

PrecoFormatado :=
VAR valor = MAX('cryptocurrencies'[current_price])
RETURN
IF(
    valor >= 1000,
    FORMAT(valor / 1000, "0.0") & "k",
    FORMAT(valor, "0.00")
)

##⚙️ Interações Personalizadas:
Visuais específicos ignoram segmentações usando “Editar Interações” no Power BI

##🚀 Como Usar
Exportar os dados do arquivo .db para .csv
Subir os arquivos .csv para o Google BigQuery
Conectar o Power BI ao BigQuery
Criar relações entre as tabelas
Aplicar transformações com Power Query
Criar medidas com DAX e os visuais conforme necessidade
Personalizar layout e interações do dashboard

##✅ Resultado Esperado
Um painel dinâmico que permite:
Acompanhamento da evolução histórica dos preços
Comparação entre diferentes criptomoedas
Identificação das moedas com maior ou menor valor
Visualização clara e interativa dos dados de mercado
