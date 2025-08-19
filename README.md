📊 Desafio-TelecomX — Parte 2 (BR)

Este repositório documenta a segunda fase do projeto da Telecom X, cujo objetivo é desenvolver modelos de Machine Learning para prevenir a evasão de clientes (churn).
O trabalho cobre desde o pré-processamento dos dados até a modelagem preditiva e interpretação dos resultados, com foco em gerar insights estratégicos que possam ser aplicados para retenção de clientes.

🎯 Objetivo

O projeto tem como metas principais:

Identificar os fatores que influenciam a evasão de clientes;

Desenvolver modelos capazes de prever quais clientes têm maior probabilidade de cancelar o serviço;

Fornecer insights que apoiem a criação de estratégias de retenção mais eficazes.

🔎 Etapas do Projeto
1. Carregamento e Exploração dos Dados

Leitura do arquivo dados_tratados.csv;

Inspeção inicial para compreender a estrutura e o conteúdo.

2. Tratamento de Dados

Remoção de linhas com valores ausentes na coluna Cancelou;

Salvamento do conjunto tratado em dados_tratados.csv.

3. Análise da Proporção de Classes

Cálculo da proporção de clientes que cancelaram (Sim) e que mantiveram o serviço (Não);

Identificação de forte desequilíbrio entre as classes.

4. Codificação de Variáveis Categóricas

Aplicação de One-Hot Encoding (pd.get_dummies);

Exclusão da coluna ID_Cliente, por não ser relevante para o modelo.

5. Análise de Correlação

Cálculo da matriz de correlação para variáveis numéricas e a variável-alvo (Cancelou_Yes);

Principais correlações encontradas:

Tipo_Internet_Fiber optic;

Metodo_Pagamento_Electronic check;

Cobranca_Mensal;

Fatura_Digital_Yes;

Meses_Permanencia (correlação negativa).

6. Análise Exploratória de Variáveis-Chave

Construção de boxplots para Meses_Permanencia e Cobranca_Total em relação ao churn;

Conclusão: clientes que cancelam tendem a apresentar menor tempo de permanência e menor valor de cobrança total.

7. Preparação para Modelagem

Separação entre variáveis independentes (X) e alvo (y);

Divisão em treino (70%) e teste (30%), com estratificação;

Aplicação do SMOTE para balanceamento das classes no conjunto de treino.

8. Modelagem Preditiva

Modelos avaliados:

Random Forest Classifier (sem normalização);

K-Nearest Neighbors (KNN) (com normalização via StandardScaler).

Etapas:

Treinamento com o conjunto balanceado;

Avaliação com métricas: precisão, recall e f1-score;

Geração de matrizes de confusão.

9. Otimização de Hiperparâmetros (Random Forest)

Utilização de GridSearchCV, otimizando para f1-macro;

Melhores parâmetros encontrados:

{
  'class_weight': 'balanced',
  'max_depth': 15,
  'min_samples_split': 2,
  'n_estimators': 100
}

10. Importância das Variáveis

As variáveis mais relevantes para prever churn foram:

Meses_Permanencia;

Cobranca_Total;

Cobranca_Mensal;

Tipo_Contrato_Two year;

Tipo_Contrato_One year;

Suporte_Tecnico_Yes;

OnlineSecurity_Yes.

📈 Resultados

Random Forest superou o KNN, principalmente no recall da classe positiva (Cancelou_Yes);

Principais fatores de evasão identificados:

Tempo de permanência;

Tipo de contrato;

Valor da cobrança;

Uso (ou não) de serviços adicionais.

💡 Estratégias Recomendadas

Criar programas de retenção focados nos primeiros meses de serviço;

Incentivar contratos de longo prazo;

Promover a adesão a serviços agregados (Suporte Técnico, Segurança Online);

Investigar as causas de evasão entre clientes de fibra óptica;

Utilizar o modelo Random Forest para identificar clientes de alto risco e oferecer ações de retenção personalizadas.

🛠️ Tecnologias Utilizadas

Python: Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, Imbalanced-learn

Jupyter Notebook

SMOTE (balanceamento)

GridSearchCV (otimização de hiperparâmetros)

📂 Estrutura de Arquivos
|-- dados_tratados.csv      # Base de dados tratada  
|-- Telecom_X_Análise_de_Evasão_de_Clientes_(parte2).ipynb  # Análises e modelagem  
|-- README.md               # Documentação do projeto  

👩‍💻 Autor

Priscilla Neri
