# Comparação de Regressão Linear Simples vs. Múltipla

1. Visão Geral do Projeto
Este projeto tem como objetivo principal comparar o poder preditivo da Regressão Linear Simples (RLS) e da Regressão Linear Múltipla (RLM) na previsão do preço de aluguel (valoraluguel).

O dataset utilizado (ALUGUEL_MOD12.csv) é composto por variáveis imobiliárias (condomínio, metragem, número de quartos, etc.). A conclusão busca justificar a escolha do modelo mais adequado para a previsão de preços de imóveis, utilizando a métrica R² (Coeficiente de Determinação) como principal indicador de desempenho.

2. Preparação Inicial de Dados
Esta seção garante que os dados estejam prontos para o treinamento dos modelos de Regressão.

Importação de Bibliotecas: Foram importadas pandas, numpy, sklearn.model_selection (para divisão de bases), sklearn.linear_model.LinearRegression e sklearn.metrics (para r2_score e mean_squared_error).

Carregamento e Limpeza de Nomes: O arquivo ALUGUEL_MOD12.csv é carregado. Os nomes das colunas são padronizados para o formato snake_case (minúsculas, sem caracteres especiais), o que é essencial para a manipulação do Pandas.

Tratamento de Nulos: A base foi verificada, e o código confirmou a ausência de valores nulos, dispensando a necessidade de imputação.

Verificação de Tipos: Todos os dados foram verificados como numéricos (int64), o que é adequado para a Regressão Linear.

3. Divisão de Bases
Definição de Variáveis:

Target (Y): valoraluguel

Features (X_RLS): Apenas valorcondominio (para Regressão Simples)

Features (X_RLM): valorcondominio, valormetragem, nquartos, nsuites, nvagas (para Regressão Múltipla)

Divisão: A base foi dividida usando train_test_split em 70% para Treino e 30% para Teste para garantir a avaliação em dados não vistos.

4. Modelo 1: Regressão Linear Simples (RLS)
A RLS utiliza apenas uma feature (valorcondominio) para prever a variável alvo (valoraluguel).

Treinamento: O modelo (model_rls) é treinado com X_train_rls e y_train.

Avaliação: O modelo é avaliado na base de teste.

Resultados:

R² (Teste): Aproximadamente 0.75.

Interpretação: Isso significa que a variação no valorcondominio sozinha explica cerca de 75% da variação no valoraluguel.

5. Modelo 2: Regressão Linear Múltipla (RLM)
A RLM utiliza cinco features (valorcondominio, valormetragem, nquartos, nsuites, nvagas) para prever a variável alvo.

Treinamento: O modelo (model_rlm) é treinado com o conjunto completo de features (X_train_rlm) e y_train.

Avaliação: O modelo é avaliado na base de teste.

Resultados:

R² (Teste): Aproximadamente 0.90.

Interpretação: A combinação das cinco features explica cerca de 90% da variação no valoraluguel.

6. Conclusão e Justificativa da Escolha

A comparação dos resultados demonstra claramente a superioridade da Regressão Linear Múltipla.

ModeloVariáveis UtilizadasR² (Teste)Poder ExplicativoRLS (Simples)1 (valorcondominio)$\approx 0.75$Explica 75% da variaçãoRLM (Múltipla)5 (Condomínio, Metragem, Quartos, etc.)$\approx 0.90$Explica 90% da variação

Justificativa do Desempenho: A previsão do preço de um aluguel é um fenômeno multifatorial. O modelo de RLM é inerentemente superior neste contexto porque consegue capturar os efeitos combinados e individuais de variáveis adicionais (como metragem e número de quartos) que têm um impacto forte e comprovado no preço. Ao incluir mais features relevantes, a RLM conseguiu reduzir o erro residual, aumentando significativamente o poder preditivo do modelo.

Recomendação Final: O modelo de Regressão Linear Múltipla deve ser o escolhido para uso, pois oferece uma precisão significativamente maior na previsão do preço de aluguel.
