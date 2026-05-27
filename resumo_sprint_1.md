# Sprint 1: Engenharia de Dados, Ingestão e Nuvem (GCP)
    ## 1. Geração de Dados Sintéticos (Python e Princípios SOLID): O   projeto começou com a construção da fundação dos dados através de scripts em Python (utilizando bibliotecas como Faker, Pandas e Numpy) para simular o comportamento de 10.000 utilizadores e as suas respetivas transações de apostas.

        O código foi desenhado com base em programação orientada a objetos e respeitando os princípios SOLID, com forte foco no Princípio de Responsabilidade Única (SRP).

        Durante esta fase, foram identificados e resolvidos de forma robusta vários problemas técnicos, como o bug de tipagem que impedia a comparação correta entre objetos datetime e timedelta no cálculo do avanço do tempo.

    ## 2. Orquestração e Ingestão de Dados (Alternativa Gratuita com Prefect): Para evitar os custos de faturação do Google Cloud Platform (GCP) sem perder o nível de engenharia exigido pela vaga, o pipeline foi adaptado para um ambiente 100% gratuito e local.

        Em vez de um script de upload simples, implementou-se o Prefect para orquestrar o fluxo de dados. O processo foi dividido num Flow contendo várias Tasks independentes (validação, infraestrutura e cópia simulada).

        Os ficheiros resultantes foram organizados numa estrutura de pastas local (gcp_storage_mock) que simula o comportamento de um bucket no Google Cloud Storage. Além disso, esta abordagem permitiu a visualização e monitorização do pipeline através do painel (dashboard) do próprio Prefect.

    ## 3. Criação do Data Warehouse e Modelagem Dimensional (SQLite): A etapa do Google BigQuery foi perfeitamente adaptada utilizando o SQLite, que vem embutido nativamente no Python e suporta a sintaxe padrão de SQL ANSI.

        Recorreu-se a scripts de Data Definition Language (DDL) para criar a base de dados aposta_ganha_dw.db e estruturar formalmente o modelo Star Schema.

        As tabelas criadas (dim_usuarios e fato_transacoes) foram configuradas com tipagem forte, definindo Chaves Primárias (Primary Keys) e Chaves Estrangeiras (Foreign Keys) para garantir a integridade dos relacionamentos entre os utilizadores e as transações no sistema.