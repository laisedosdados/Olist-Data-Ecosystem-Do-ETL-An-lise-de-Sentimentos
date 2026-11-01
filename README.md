# 🛒 Olist Data Ecosystem: Do ETL à Análise de Sentimentos

Projeto **End-to-End** de dados aplicado ao e-commerce brasileiro, usando a base pública da Olist: da engenharia de dados ao fine-tuning de um modelo de linguagem em português.

## Destaque: análise de sentimentos com BERTimbau

Classificador de reviews de clientes (positivo ou negativo) treinado com 32 mil comentários reais em português.

**Modelo publicado:** [laisedosdados/bertimbau-sentimento-olist](https://huggingface.co/laisedosdados/bertimbau-sentimento-olist)

### Resultados (conjunto de teste, 3.244 comentários)

| Modelo | F1-macro | Acurácia | Erros |
|---|---|---|---|
| TF-IDF + Regressão Logística (baseline) | 0,907 | 91,6% | 271 |
| **BERTimbau com fine-tuning** | **0,933** | **94,1%** | **192 (−29%)** |

### Principais achados

- **Entender negação é o diferencial:** palavras como "não" aparecem em 27% dos comentários, mas em 54% dos casos que só o BERTimbau acertou. Ele entende frases como "ainda não testei, mas parece ótimo", que o baseline classifica como negativas.
- **Parte do erro é do dado, não do modelo:** entre os 20 erros mais confiantes dos dois modelos, 13 tinham rótulo inconsistente com o texto (como "não recebi o produto" com nota alta) e 7 tinham sentimento misto.
- **A entrega move a satisfação:** os termos mais negativos falam de entrega ("não recebi", "aguardando", "demora") e os mais positivos, de rapidez ("antes do prazo", "rápido").

### Decisões técnicas

- Rótulo a partir da nota (1–2 negativo, 4–5 positivo); nota 3 excluída por ser ambígua.
- Remoção de textos duplicados para evitar **vazamento** entre treino e teste.
- Stopwords mantidas, porque remover "não" inverteria o sentido de "não gostei".
- Divisão 80/10/10 estratificada, com seed fixa para reprodutibilidade; o teste só foi usado na avaliação final.
- F1-macro como métrica principal, por causa do desbalanceamento (68% positivos).
- Treino de 2 épocas (3min49s numa GPU T4). Na segunda época a loss de validação começou a subir, um sinal inicial de overfitting, por isso o treino não foi estendido.

---

## Arquitetura do projeto

### 1. Engenharia de Dados (ETL) — `01_engenharia_de_dados.ipynb`
Unificação das tabelas relacionais da Olist (pedidos, itens, avaliações, pagamentos, clientes e produtos), tratamento de nulos e criação de atributos como tempo de entrega e atraso.

### 2. Análise de Sentimentos (NLP) — `02_analise_de_sentimentos.ipynb`
Baseline com TF-IDF, fine-tuning do BERTimbau, avaliação no conjunto de teste e análise de erros.

### 3. Próximas fases
- Análise exploratória de negócios: atrasos por estado, sazonalidade e relação entre frete e satisfação.
- Modelo de previsão de atraso no momento da compra.
- Classe neutra no classificador de sentimentos e comparação com um LLM via prompt (zero-shot).

---

## Stack
- **Linguagem:** Python
- **Dados:** pandas, SQL (lógica relacional)
- **Machine Learning:** scikit-learn
- **NLP:** Hugging Face Transformers, Datasets, BERTimbau
- **Ambiente:** Jupyter Notebook, Google Colab (GPU T4)

## Status
- [x] Fase 1: ETL e unificação das tabelas
- [x] Fase 4: Análise de sentimentos com BERTimbau
- [ ] Fase 2: Análise exploratória de negócios
- [ ] Fase 3: Modelo de previsão de atrasos

## Como reproduzir
O notebook 02 foi executado no Google Colab com GPU. A primeira célula recarrega os dados e baixa o modelo treinado do Hugging Face, sem precisar treinar de novo.
