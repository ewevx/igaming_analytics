# Sprint 2: Manipulação de Dados Avançada e SQL
    # 1. Qualidade e Limpeza de Dados (schema_setup.sql):

            A sprint começou com o foco em garantir a integridade das informações armazenadas na base de dados SQLite (aposta_ganha_dw.db).

            Foi feito o tratamento de valores nulos (garantindo que os valores monetários em falta passassem a 0.0) e a padronização de campos de texto (como a formatação de maiúsculas e minúsculas nas categorias).

            Criou-se a tabela vw_transacoes_limpas, unindo a Tabela Fato de transações com a Tabela Dimensão de utilizadores, de forma a evitar a repetição de JOINs nas consultas seguintes.

            Nesta etapa, resolveu-se um problema de localização de ficheiros através da implementação de um script com um localizador dinâmico, que procura automaticamente a base de dados na raiz do projeto.

    # 2. Engenharia de Features e Agregação Avançada (feature_aggregation.sql):

            Em vez de processar os dados em Python, aplicou-se SQL puro e avançado, tirando partido de Window Functions (LAG OVER PARTITION BY) e agregações condicionais (SUM CASE WHEN).

            Através destas ferramentas, foram calculadas três variáveis de negócio fundamentais para o setor do iGaming:


                Recency: Os dias decorridos desde a última aposta, essencial para prever o Churn (abandono da plataforma).


                Deposit Velocity: A frequência média com que o utilizador faz depósitos.


                Chasing Losses: A identificação de comportamentos de risco onde o utilizador faz um depósito imediatamente após ter perdido uma aposta (focado no Jogo Responsável).

            A variável alvo para o modelo preditivo (target_churn) foi também criada e incorporada diretamente na base.

            Durante a construção desta query massiva, foram identificados e corrigidos erros clássicos de sintaxe, como a falta de vírgulas nas funções ROUND e gralhas nos nomes das colunas.