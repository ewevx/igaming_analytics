# iGaming Analytics Framework — Predição de Churn & Monitoramento de Risco (Aposta Ganha)

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![SQLite](https://img.shields.io/badge/sqlite-%2307405e.svg?style=for-the-badge&logo=sqlite&logoColor=white)
![Power Bi](https://img.shields.io/badge/power_bi-F2C811?style=for-the-badge&logo=power-bi&logoColor=black)
![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)

# Visão Geral do Projeto

No competitivo mercado de iGaming (Apostas Esportivas e Cassino Online), o custo de aquisição de cliente (CAC) é historicamente elevado, tornando a **retenção ativa** e o aumento do **LTV (Lifetime Value)** os principais pilares de lucratividade de uma operadora.

Este projeto desenvolve um **Framework de Analytics ponta a ponta** customizado para o modelo de negócios da **Aposta Ganha**. O ecossistema combina Engenharia de Dados, Inteligência Artificial (Aprendizado Não-Supervisionado) e Business Intelligence para solucionar duas dores críticas do setor:
1. **Minimização de Churn:** Identificação preditiva de usuários com alta propensão de evasão da plataforma.
2. **Compliance & Jogo Responsável:** Detecção automatizada de padrões de comportamento compulsivo ou anomalias financeiras para proteção ao jogador e blindagem jurídica da marca.

---

# Componentes do Pipeline

**Data Warehouse (SQLite):** Armazenamento estruturado e centralizado do histórico de comportamento transacional do banco corporativo aposta_ganha_dw.db.

**Machine Learning Pipeline (Scikit-Learn):** Treinamento e aplicação do algoritmo K-Means para segmentação de perfis com base nas variáveis-chave de engajamento e risco: volume_deposito, saldo_apostas, deposit_velocity, chasing_losses_events e recency.

**Data Integration Pipeline (ETL):** Processo que limpa os estados voláteis, valida os caminhos do banco de dados, consolida os índices de IA gerados e exporta o datastore final analytics_outputs.csv.

**Dashboard de Monitoramento Executivo (Power BI):** Camada de BI conectada diretamente aos dados finais processados, equipada com medidas DAX e inteligência de "Alerta Vermelho".

---

# O Dashboard Executivo e Sistema de Alerta Vermelho

O painel foi projetado sob os conceitos de UX/UI analíticos, garantindo que o time de compliance e a diretoria identifiques riscos operacionais e anomalias de forma instantânea.

---

## KPIs de iGaming Implementados (Métricas DAX) 

**GGR (Gross Gaming Revenue):** O indicador financeiro vital do setor. Mede o lucro bruto gerado pelas apostas, subtraindo as retiradas da plataforma.

**Churn Rate (%):** Taxa percentual dinâmica que calcula o volume de usuários classificados com comportamento de abandono iminente.

**Ticket Médio de Depósito:** Monitoramento da densidade financeira média por transação de aporte na plataforma.

**Status de Alerta de Risco:** Medida lógica que atua como gatilho para os sinalizadores da tela.

---

# Regras Visuais e Condicionais de Compliance

**Gatilho no KPI Card:** O cartão que exibe a Qtd Usuários Alto Risco possui uma formatação condicional baseada em regras. Se o valor for maior que zero, o plano de fundo do componente altera automaticamente para Vermelho de Segurança, sinalizando a necessidade de intervenção imediata do time de compliance.

**Eixos Individuais de Anomalia (Não-Resumidos):** O Gráfico de Dispersão foi configurado para Não Resumir as métricas de deposit_velocity e chasing_losses_events. Isso permite isolar o comportamento individual de cada user_id na base, mapeando anomalias financeiras e indicativos de compulsividade em tempo real.

**Consistência Visual de Risco:** Filtros estratégicos (Perfil_Risco) substituem os identificadores numéricos puros da inteligência artificial por categorias funcionais de negócio. A cor Vermelha é tratada de forma exclusiva e restrita para destacar o perfil de risco tanto no mapa de dispersão quanto no gráfico de distribuição.

---

# Perfilamento dos Clusters Identificados pela IA

AO algoritmo de Machine Learning segmentou com precisão a base de clientes em 4 perfis comportamentais distintos, permitindo estratégias direcionadas dos times de CRM e Compliance:

**Cluster 0 — Recreativo:** Representa a maior fatia de usuários. Apresenta baixo volume financeiro transacionado, comportamento de entretenimento controlado e zero ocorrências de chasing losses. (Estratégia: Campanhas de engajamento padrão e incentivo de fidelidade).

**Cluster 1 — Alto Risco (Compulsivo):** Usuários identificados por uma altíssima velocidade de depósitos em janelas curtas de tempo combinada com episódios frequentes de chasing losses (tentativa desesperada de recuperar prejuízos). (Estratégia: Acionamento imediato do protocolo de Jogo Responsável, limitação preventiva ou bloqueio temporário da conta).

**Cluster 2 — Desengajado/Inativo:** Usuários que pararam de interagir com a plataforma, caracterizados por uma métrica de recency criticamente elevada. (Estratégia: Réguas de reativação agressivas via CRM com incentivos de bônus freebet).

**Cluster 3 — VIP:** Clientes de altíssimo valor de mercado, com grande volume de aportes financeiros e saldos estáveis consolidados na plataforma. (Estratégia: Atendimento personalizado premium e encaminhamento para gerentes de contas dedicados).

---

**Estrutura de Pastas e Como Executar** 
**Organização do Repositório**

aposta-ganha-analytics-framework/
│
├── data/
│   └── processed/
│       └── analytics_outputs.csv       # Datastore final consolidado que alimenta o BI
│
├── src/
│   ├── data_generation/
│   │   └── data_integration.ipynb      # Script de consolidação e ETL do Data Warehouse
│   │
│   └── machine_learning/
│       └── train_clustering.ipynb      # Pipeline de Machine Learning e treino do K-Means
│
├── aposta_ganha_bi.pbix                # Arquivo do Dashboard Interativo do Power BI
├── aposta_ganha_dw.db                  # Banco de Dados SQLite corporativo unificado
└── README.md                           # Documentação e Visão Geral do Framework

---

# Passos para Execução

Configuração do Ambiente: Instale as dependências analíticas fundamentais do projeto:

``Bash   pip install pandas numpy notebook scikit-learn matplotlib seaborn

**Processamento de Machine Learning:** Execute o notebook de segmentação para ler os dados analíticos históricos, rodar o modelo K-Means e persistir os resultados estruturados na tabela de produção tabela_final_modelada dentro do SQLite.

src/machine_learning/train_clustering.ipynb

**Consolidação do Pipeline (ETL):** Execute o script de integração de dados para sincronizar os caminhos absolutos, ler os novos clusters gerados pela inteligência artificial e atualizar o arquivo de saída tratado:

src/data_generation/data_integration.ipynb

**Exploração de Insights e Alertas:** Abra o arquivo aposta_ganha_bi.pbix no seu Power BI Desktop para analisar as dispersões individuais de risco, testar as formatações dinâmicas de segurança e gerar filtros refinados por estado.