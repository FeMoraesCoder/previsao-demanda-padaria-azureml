# Previsão de Demanda de Pão Francês com Azure Machine Learning

## 🎯 Objetivo do Projeto
Desenvolver um modelo de regressão preditiva utilizando o Microsoft Azure Machine Learning para prever a quantidade ideal de pães franceses a serem produzidos por período. O objetivo de negócio é evitar o desperdício de insumos e garantir a satisfação do cliente (evitando a falta de pão ou a venda de pão frio em horários de baixa demanda).

## 🛠️ Tecnologias e Ferramentas Utilizadas
- **Microsoft Azure Machine Learning Studio**
- **Automated ML (AutoML)** com restrição de tempo (15 minutos) e algoritmo `XGBoostRegressor`.
- **Azure ML Designer** para criação visual de um pipeline de regressão linear.
- **MLflow** para registro e rastreamento das métricas dos experimentos.

## 🚀 Etapas de Implementação

1. **Preparação do Ambiente e Dados:** Criação de um Workspace no Azure, provisionamento de instâncias e clusters de computação de baixo custo e ingestão do dataset simulado `dados_padaria.csv`.

2. **Criação do Pipeline no Designer:**
   Foi construído um pipeline estruturado contendo as etapas de seleção de colunas, divisão de dados (Split de 80/20), treinamento com `Linear Regression`, além de escoragem e avaliação do modelo.
   *(Adicione aqui a imagem do seu pipeline visual)*
   `![Pipeline](prints/01_pipeline_designer.png)`

3. **Treinamento Automatizado (AutoML):**
   Configuração de um job automatizado focado em prever a coluna `paes_vendidos`. Foram aplicados limites estritos de custo (15 minutos) e seleção específica do algoritmo XGBoost, garantindo um balanço entre performance e consumo de nuvem.
   *(Adicione aqui a imagem do resultado do AutoML)*
   `![AutoML](prints/02_automl_xgboost.png)`

4. **Implantação (Deploy em Tempo Real):**
   O modelo vencedor foi implantado como um Endpoint online. Testes foram realizados enviando requisições em tempo real para prever a demanda com base na temperatura, dia da semana e eventos externos.
   *(Adicione aqui a imagem do teste do Endpoint)*
   `![Endpoint](prints/03_endpoint_teste.png)`

## 💡 Insights e Aprendizados
- **Gestão de Custos:** A importância de provisionar clusters com zero nós mínimos de ociosidade e a exclusão imediata de endpoints após os testes.
- **AutoML vs Designer:** O AutoML agiliza a escolha dos melhores hiperparâmetros e algoritmos (como o XGBoost), enquanto o Designer oferece uma visão clara e didática de cada etapa da transformação dos dados.
- **Variáveis de Impacto:** Fatores externos, como entrada e saída escolar, demonstraram forte correlação com os picos de demanda no modelo desenvolvido.
