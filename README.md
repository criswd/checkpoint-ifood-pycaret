# Checkpoint CP1 – iFood: Classificação com PyCaret

## 👨‍🎓 Alunos
- RM555992 – Cristiano Washington Dias  
- RM558108 – Thiago Almança da Silva  

## 📌 Objetivo
Desenvolver um modelo de classificação para prever a resposta dos clientes a campanhas promocionais da empresa iFood, utilizando a biblioteca **PyCaret** com foco na métrica **AUC (Área sob a Curva ROC)**.

---

## ⚙️ Etapas Realizadas

1. **Importação e limpeza de dados**  
   - Remoção de colunas irrelevantes e amostras com `NaN`
   - Conversão de tipos de dados

2. **Criação de novas features**  
   - `Total_Spent`: soma de todos os produtos adquiridos  
   - `Age_Group`: faixa etária do cliente  
   - `Avg_Spent_per_Month`: gasto médio mensal  

3. **Split dos dados**  
   - 95% treino + 5% conjunto de validação (`df_valid`)

4. **Setup do PyCaret**  
   - Remoção de outliers, normalização e seleção de features  
   - Correção de desbalanceamento com **SMOTE**

5. **Comparação entre modelos (`compare_models`)**  
   - Melhor AUC obtido com `Logistic Regression` (0.834)

6. **Tuning do modelo (`tune_model`)**  
   - Leve ajuste nos parâmetros com melhoria de estabilidade

7. **Avaliação visual (`plot_model`)**  
   - Curva ROC, Matriz de confusão e Feature Importance

8. **Validação final (`predict_model` com `df_valid`)**  
   - Resultado: AUC = **0.6484** no conjunto de validação

---

## 📈 Modelo Final

- **Modelo:** Logistic Regression (tune_model)  
- **AUC (treino):** 0.8344  
- **AUC (validação):** 0.6484  
- **Features mais relevantes:**  
  - `Recency`, `Time_Customer`, `MntMeatProducts`, `Total_Spent`, `Avg_Spent_per_Month`

---

## 🔗 Links

- 📓 Notebook no Colab: [Acessar](https://colab.research.google.com/drive/1Tl3wDeVi_1gYCofGjFRZi0TzNDA-n8bI?usp=sharing)  
- 🐙 Repositório no GitHub: [Acessar](https://github.com/criswd/checkpoint-ifood-pycaret/)  

---

## 🧪 Resultado exemplo

| prediction_label | prediction_score |
|------------------|------------------|
| 0                | 0.7464           |
| 1                | 0.8104           |
| 0                | 0.8992           |
| 0                | 0.8164           |
| 1                | 0.9808           |

---

## ▶️ Como Executar
1. Acesse o notebook via Google Colab
2. Instale as dependências (`!pip install pycaret`)
3. Execute célula por célula para replicar o experimento
