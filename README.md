# PowerBI_Projects
All my Business Intellingence projects using Power BI. 

Aqui você encontra meu portifólio de projetos de Business Intelligence (BI)


#  Case Spotify Description


![Descrição da Imagem](https://github.com/reearantes/PowerBI_Projects/blob/main/case_sf.png)

My template on Figma Here:
https://www.figma.com/community/file/1301631027349874475

The dashboard Covers:
 - 💠Enriched dataset with ChatGPT & Python - Conjunto de dados enriquecido com ChatGPT & Python.
 - 💠Glassmorphism Background - Antecedentes de Glomorfismo.
 - 💠Power BI Building - Construção do Power BI.
 - 💠Figma Cover Art - Background no figma.
 - 💠DENEB Visuals - Visual costumizado.
 - 💠PBI Format.

Full tutorial : https://www.youtube.com/watch?v=ZSrVOyKAC4Y&feature=youtu.be


# **  Dashboard Financeiro**

![Descrição da Imagem](https://github.com/reearantes/PowerBI_Projects/raw/main/01_VisaoGeral.jpg)

![Descrição da Imagem](https://github.com/reearantes/PowerBI_Projects/blob/main/02_Fluxo_Caixa.jpg)

## **Visão Geral**

O **Dashboard Financeiro** foi desenvolvido para analisar a movimentação financeira de uma empresa, com foco em receitas, custos, despesas, lucros e seus detalhes. O objetivo é fornecer insights claros e acionáveis para auxiliar na tomada de decisões estratégicas.

### **Contexto**

- **Área**: Financeira.
- **Início das atividades**: 2017.
- **Fonte de dados**: Arquivos Parquet (dados tratados em Python).
- **Principais análises**:
  - Receita por mês vs. mês do ano anterior.
  - Receita por tipo de conta.
  - Pagamento por tipo de conta.
  - Pagamento por tipo e mês.
  - Receita por cliente.
  - Fluxo de caixa por mês em gráfico de cascata e detalhada em tabela (tela dedicada).

---

## **Modelagem dos Dados**

O projeto utiliza um modelo de dados **Star Schema**, que consiste em uma tabela de fato central relacionada a várias tabelas de dimensão. Esse modelo é ideal para análises eficientes e consultas rápidas.

### **Tabelas**

#### **1. Tabela: Contas (Dimensão)**
- **Descrição**: Armazena informações descritivas sobre as contas, como tipo e movimento.
- **Campos**:
  - `id`: Identificador único da conta.
  - `movimento`: Tipo de movimento (entrada/saída).
  - `lancamento`: Descrição do lançamento.
  - `conta`: Nome da conta.
  - `tipo`: Categoria da conta (receita, despesa, custo, etc.).

#### **2. Tabela: Recebimentos (Fato)**
- **Descrição**: Contém os valores recebidos pela empresa, divididos em vários arquivos por ano.
- **Campos**:
  - `data`: Data do recebimento.
  - `plano_contas_id`: Chave estrangeira para a tabela de contas.
  - `cliente`: Nome do cliente.
  - `uf`: Estado onde o cliente está localizado.
  - `valor_recebido`: Valor recebido.

#### **3. Tabela: Pagamentos (Fato)**
- **Descrição**: Contém os valores pagos pela empresa, divididos em vários arquivos por ano.
- **Campos**:
  - `ID Conta`: Chave estrangeira para a tabela de contas.
  - Colunas por ano (exemplo: `2023`, `2024`) com os valores de pagamento.

#### **4. Tabela: Calendário (Dimensão)**
- **Descrição**: Fornece contexto temporal para as análises.
- **Campos**:
  - `data`: Data no formato `dd/MM/yyyy`.
  - `Ano`: Ano da data.
  - `Mês`: Número do mês.
  - `Nome do Mês`: Nome do mês em português.
  - `Trimestre`: Trimestre do ano.
  - `Semana do Ano`: Número da semana no ano.
  - `Dia da Semana`: Número do dia da semana.
  - `Nome do Dia da Semana`: Nome do dia da semana em português.
  - `Dia do Mês`: Dia do mês.
  - `Dia do Ano`: Dia do ano.
  - `Fim de Semana`: Indica se a data é um fim de semana ("Sim" ou "Não").
  - `AnoMês`: Ano e mês no formato `AAAAMM` (exemplo: `202301` para janeiro de 2023).

---

## **ETL (Extract, Transform, Load)**

O processo de ETL foi realizado em Python para garantir a qualidade e consistência dos dados. As principais etapas foram:

1. **Extração**:
   - Leitura dos arquivos Parquet contendo dados de recebimentos e pagamentos.

2. **Transformação**:
   - Tratamento de dados ausentes ou inconsistentes.
   - Agregação dos dados por ano, mês e tipo de conta.
   - Criação de uma tabela de calendário para fornecer contexto temporal.

3. **Carga**:
   - Exportação dos dados tratados para o Power BI, onde foram criados os relacionamentos e o dashboard.

---

## **Modelo Star Schema**

O modelo de dados utilizado é o **Star Schema**, que consiste em:

- **Tabelas de Fato**:
  - `Recebimentos`: Armazena os valores recebidos.
  - `Pagamentos`: Armazena os valores pagos.

- **Tabelas de Dimensão**:
  - `Contas`: Fornece contexto sobre as contas.
  - `Calendário`: Fornece contexto temporal.

### **Relacionamentos**

- As tabelas de fato (`Recebimentos` e `Pagamentos`) se relacionam com a tabela de dimensão `Contas` através da chave `ID Conta`.
- As tabelas de fato também se relacionam com a tabela de dimensão `Calendário` através da coluna `data`.

---

## **Visualizações do Dashboard**

O dashboard foi projetado para fornecer insights claros e acionáveis. As principais visualizações incluem:

1. **Receita por Mês vs. Mês do Ano Anterior**:
   - Comparação da receita mensal com o mesmo mês do ano anterior.

2. **Receita por Tipo de Conta**:
   - Distribuição da receita por categoria de conta.

3. **Pagamento por Tipo de Conta**:
   - Distribuição dos pagamentos por categoria de conta.

4. **Pagamento por Tipo e Mês**:
   - Detalhamento dos pagamentos por tipo de conta e mês.

5. **Receita por Cliente**:
   - Receita agregada por cliente.

6. **Fluxo de Caixa por Mês**:
   - Gráfico de cascata mostrando o fluxo de caixa mensal.
   - Tabela detalhada com os valores de entrada e saída.

---

## **Tecnologias Utilizadas**

- **Python**: Para tratamento e transformação dos dados.
- **Power BI**: Para criação do dashboard e visualizações interativas.
- **Parquet**: Formato de arquivo utilizado para armazenar os dados tratados.

---

## **Como Executar o Projeto**

1. **Pré-requisitos**:
   - Python 3.x instalado.
   - Power BI Desktop instalado.
   - Bibliotecas Python: `pandas`, `pyarrow`.

2. **Passos**:
   - Clone o repositório do GitHub.
   - Execute o script Python para tratar os dados e gerar os arquivos Parquet.
   - Abra o arquivo do Power BI e configure os relacionamentos entre as tabelas.
   - Explore as visualizações no dashboard.
