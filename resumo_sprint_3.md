# Sprint 3: Modelagem preditiva (K-Means)
    ## 1. Modelo de Predição de Churn (Aprendizado Supervisionado):
       
        Objetivo: Identificar usuários com alta probabilidade de abandonar a plataforma nos próximos 14 dias.

        Engenharia de Recursos: Utilizou-se pd.get_dummies para tratar variáveis categóricas (estado e preferência de jogo) e realizar a transformação necessária para o modelo.

        Otimização de Negócio: Em vez de usar técnicas genéricas, aplicou-se o parâmetro scale_pos_weight no XGBoost para realizar o balanceamento nativo das classes, garantindo o foco total na métrica de Recall (essencial para não perder clientes VIP em risco).

        Resultado Visual: O modelo atingiu um desempenho robusto (conforme verificado na matriz de confusão e relatório de classificação), identificando com precisão os usuários em risco e ranqueando as variáveis mais importantes (como total_apostas).

    ## 2. Modelo de Jogo Responsável (Aprendizado Não Supervisionado):
        
        Objetivo: Segmentar a base de usuários para identificar comportamentos de risco financeiro e compulsão.

        Algoritmo: Utilizou-se o K-Means para agrupar perfis comportamentais com base em variáveis estratégicas criadas na Semana 2, como deposit_velocity e chasing_losses_events.

        Técnica Robusta: Aplicou-se o StandardScaler para garantir que as escalas de dinheiro (R$) e frequência de eventos não enviesassem a clusterização, garantindo rigor estatístico.

        Visão de Negócio: O perfilamento resultante permitiu isolar o "Jogador Compulsivo" (alto risco de endividamento) do "Jogador VIP" (lucratividade estável), criando personas claras para o time de Compliance e Marketing.

    ## 3. Integração e Consolidação (Finalização do Pipeline):
        
        Para garantir que o trabalho não ficasse restrito a testes locais, desenvolveu-se o script de integração final para salvar o output (analytics_outputs.csv e tabela_final_modelada no banco SQLite).

        Este passo foi crucial para converter "experimentos de notebook" em uma Tabela de alta performance, pronta para ser consumida pelo Power BI.