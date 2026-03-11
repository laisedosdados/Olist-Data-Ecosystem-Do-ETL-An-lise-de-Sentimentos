# 🛒 Olist Data Ecosystem: Do ETL à Análise de Sentimentos

Este é um projeto **End-to-End (Ponta a Ponta)** de dados aplicado ao setor de Varejo e E-commerce. Utilizando a base de dados pública da Olist (a maior loja de departamentos dos marketplaces brasileiros), eu construo um pipeline completo passando por Engenharia de Dados, Análise de Negócios e Inteligência Artificial (NLP e Machine Learning).

## 📌 Meu Objetivo
Transformar dados brutos e fragmentados de logística, vendas e avaliações de clientes em insights acionáveis e modelos preditivos, demonstrando domínio sobre o ciclo de vida completo do dado.

---

## 🏗️ A Arquitetura do Projeto (3 Pilares)

### 1. Engenharia de Dados (ETL)
A base original é composta por 9 tabelas relacionais isoladas (Clientes, Pedidos, Pagamentos, Produtos, Vendedores, Avaliações, etc.).
* **O Desafio:** Construir um pipeline de Extração, Transformação e Carga (ETL).
* **A Solução:** Utilização de junções complexas (`JOINs`), tratamento de chaves primárias/estrangeiras e formatação de dados temporais para unificar a base e criar um repositório analítico limpo.

### 2. Análise de Dados e Business Intelligence (EDA)
Com os dados unificados, o foco muda para responder perguntas críticas de negócio:
* Mapeamento de gargalos logísticos: Quais rotas e estados sofrem com mais atrasos?
* Análise de Sazonalidade: Como datas comemorativas impactam o volume de vendas e o tempo de entrega?
* Relação entre tempo de frete e a nota de satisfação (CSAT) do consumidor brasileiro.

### 3. Ciência de Dados e NLP (Inteligência Artificial)
Aplicação de modelos preditivos para antecipar problemas e entender o cliente:
* **Previsão de Atrasos:** Treinamento de um modelo de Machine Learning capaz de prever, no momento da compra, se o pedido sofrerá atraso logístico.
* **Análise de Sentimentos (NLP):** Processamento de Linguagem Natural aplicado aos comentários e avaliações reais dos clientes para classificar o sentimento (Positivo, Neutro ou Negativo) e extrair os principais motivos de insatisfação.

---

## 🛠️ Stack Tecnológica
* **Linguagem:** Python 3.x
* **Engenharia de Dados (ETL):** Pandas, SQL (lógica relacional).
* **Análise Visual:** Matplotlib, Seaborn.
* **Machine Learning & NLP:** Scikit-Learn, NLTK/Spacy (Processamento de Texto).
* **Ambiente:** VS Code & Jupyter Notebook.

---

## 📈 Status do Projeto
- [x] Criação do repositório e estruturação do README.
- [ ] Fase 1: ETL e unificação das 9 tabelas relacionais (Engenharia de Dados).
- [ ] Fase 2: Análise Exploratória de Negócios (EDA).
- [ ] Fase 3: Modelo Preditivo de Atrasos Logísticos.
- [ ] Fase 4: Processamento de Linguagem Natural (NLP) em Avaliações.