# Checkpoint CP1 – iFood: Classificação com PyCaret

## 👨‍🎓 Alunos
- RM555992 – Cristiano Washington Dias  
- RM558108 – Thiago Almança da Silva  

## 🎯 Objetivo
Aprimorar modelos de classificação para prever a resposta dos clientes às campanhas promocionais da empresa iFood, utilizando a biblioteca **PyCaret** com foco na métrica **AUC (Área sob a Curva ROC)**.

---

## ⚙️ Etapas Realizadas

1. **Importação e limpeza de dados**
   - Remoção de colunas irrelevantes e valores ausentes
   - Conversão de tipos e normalização de categorias

2. **Criação de novas features**
   - `Total_Spent`: soma dos produtos adquiridos
   - `Age_Group`: faixa etária categorizada
   - `Avg_Spent_per_Month`: média de gastos por mês
   - `Total_Children`: soma de `Kidhome` e `Teenhome`
   - `Total_Purchases`: soma de compras web, catálogo e loja
   - `Income_per_Person`: renda dividida por número de dependentes

3. **Divisão dos dados**
   - 95% para treino/teste (`df_train_test`) e 5% para validação (`df_valid`)

4. **Modelagem com PyCaret**
   - Aplicação de `setup()` com seleção de features, balanceamento e normalização
   - Comparação entre modelos com `compare_models()`
   - Tunagem com `tune_model()` para otimização da AUC
   - Avaliação gráfica com `plot_model()`
   - Predição no conjunto de validação com `predict_model()`

---

## 🧪 Evolução dos Modelos Testados

### 1. **Regressão Logística (baseline)**

| Métrica   | Valor   |
|-----------|---------|
| AUC       | 0.6484  |
| Recall    | 0.5714  |
| F1-score  | 0.2712  |

➡️ Modelo inicial, interpretável, porém com desempenho limitado.

---

### 2. **Random Forest (v1)**

| Métrica   | Valor   |
|-----------|---------|
| AUC       | 0.8388  |
| Recall    | 0.5411  |
| F1-score  | 0.4866  |

➡️ Modelo mais robusto, com melhora significativa sobre o baseline.

---

### 3. **LightGBM Tunado (modelo final)**

| Métrica   | Valor   |
|-----------|---------|
| **AUC**   | **0.8880** ✅ |
| Recall    | 0.7143  |
| F1-score  | 0.5263  |
| Accuracy  | 0.8364  |

➡️ Modelo final escolhido, com excelente equilíbrio entre AUC e métricas de classificação.

---

## 📊 Comparativo com o modelo original (Random Forest)

| Modelo                | AUC     | F1     | Recall | Accuracy |
|-----------------------|---------|--------|--------|----------|
| Modelo Original (RF)  | 0.8983  | 0.4768 | 0.3789 | 0.8746   |
| Nosso Final (LightGBM Tunado) | **0.8880**  | **0.5263** | **0.7143** | 0.8364   |

> Embora a AUC do modelo original ainda seja ligeiramente superior, nosso modelo entrega um **Recall muito maior**, além de **F1 e precisão mais equilibradas**, sendo mais indicado para campanhas com foco em alcance de público engajado.

---

## 📈 Exemplo de Previsões

| prediction_label | prediction_score |
|------------------|------------------|
| 0                | 0.8866           |
| 0                | 0.8744           |
| 0                | 0.8980           |
| 0                | 0.9642           |
| 1                | 0.6416           |

---

## 🔍 Possíveis Melhorias Futuras

- Explorar modelos com tuning por `optuna` ou `bayesian optimization`
- Realizar **feature selection manual** com análise de SHAP/Permutação
- Implementar **validação temporal** para cenários reais
- Integrar com estratégias de marketing direto segmentado

---

## 🔗 Links

- 📓 Notebook no Colab: [Acessar](https://colab.research.google.com/drive/1Tl3wDeVi_1gYCofGjFRZi0TzNDA-n8bI?usp=sharing)  
- 🐙 Repositório no GitHub: [Acessar](https://github.com/criswd/checkpoint-ifood-pycaret/)

---

## ▶️ Como Executar
1. Acesse o notebook via Google Colab
2. Instale o PyCaret: `!pip install pycaret`
3. Execute célula por célula para replicar o experimento
