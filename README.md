# Brainstorm sobre os dados da CESB

Durante a análise dos dados da CESB é possível identificar que existem dados de vários periodos de anos. Embaixo, estão as tabelas identificadas como principais, suas descrições e observações sobre o formato dos dados.

## MySQL Safras 2019 a 2018

**inscricao:** Contém informações sobre as inscrições no desafio, incluindo dados do produtor, consultor, safra, propriedade, área, localização e categoria. Esta tabela é central, pois conecta muitas outras informações.

**colheita:** Contém dados de colheita, como data da colheita, ciclo cultural, área colhida, peso bruto, percentual de impurezas e umidade, e produtividade. Essencial para avaliar os resultados do desafio.

**implantacao:** Detalhes sobre a implantação da cultura, incluindo cultivar, espaçamento, população de plantas, data de semeadura, etc. Importante para entender as práticas agrícolas iniciais.

**adubacao:** Informações sobre a adubação realizada, tipos de adubo, doses, formas de aplicação e estádios fenológicos. Crucial para analisar o manejo nutricional.

**aplicacao_agroquimico:** Dados sobre a aplicação de agroquímicos, incluindo emergência, estádio fenológico, forma de aplicação e volume de calda. Relevante para entender o manejo fitossanitário.

**agroquimico:** Informações sobre os agroquímicos específicos utilizados, tipo, nome, dose, unidade e fabricante. Complementa a tabela aplicacao_agroquimico.

**solo:** Detalhes sobre as características do solo, textura, teor de argila, classificação e histórico de correção. Fundamental para entender o ambiente de cultivo.

**safra:** Informações sobre as safras do desafio, incluindo ano e períodos de inscrição. Essencial para contextualizar os dados por safra.
cultivar: Cadastro das cultivares utilizadas. Permite analisar o impacto da cultivar na produtividade.

**fornecedor:** Cadastro dos fornecedores de produtos. Pode ser útil para analisar a relação entre fornecedores e práticas agrícolas/resultados.

**pessoa:** Informações gerais sobre as pessoas envolvidas (produtores, consultores, etc.). Permite vincular dados de outras tabelas a indivíduos.

**estado:** Cadastro dos estados brasileiros e suas regiões. Permite análises geográficas.

> Essas tabelas parecem ser as mais relevantes para entender o contexto do desafio de produtividade e analisar os fatores que influenciam a colheita. As tabelas wp_ parecem estar mais relacionadas à estrutura do site WordPress e podem ser menos relevantes para a análise agrícola principal, a menos que haja um interesse específico em dados de usuários ou conteúdo do site. As tabelas old_ provavelmente contêm dados de versões anteriores e podem ser úteis para análises históricas, mas as tabelas sem o prefixo old_ parecem ser as fontes de dados mais atuais e completas.



## MySQL Safras 2021 a 2024

**inscricao_desafio**: Registra as inscrições/entradas no desafio a partir de 2021. É a tabela central do período, com mais de 7.700 registros, conectando produtores/consultores, safras, categorias e etapas do processo. Serve como ponto de junção entre dados de campo, colheita, pagamentos e auditorias.

**campo_de_producao**: Consolida medições detalhadas de campo (ex.: estande, altura de plantas, vagens por planta, coordenadas, áreas auditadas). É rica em métricas agronômicas, mas apresenta alta variabilidade e sinais de problemas de qualidade de dados em algumas colunas (por exemplo, médias e desvios muito altos em media_vagens_por_planta e populacao_plantas_calculada, sugerindo erros de unidade ou outliers). Alguns campos aparentam subutilização (ex.: area_auditada_medicao_01 e certos IDs de equipamentos).

**agroquimico / aplicacao_agroquimico**: Mantêm o detalhamento de produtos utilizados e suas aplicações no campo, incluindo tipo, dose, unidade, fabricante, estádio fenológico, forma e volume de aplicação. Relevantes para traçar o manejo fitossanitário e possíveis correlações com produtividade e custos.

**adubacao**: Descreve insumos e práticas de adubação (tipos, doses, épocas/estádios de aplicação). Fundamental para avaliar manejo nutricional e relacionar com resultados de campo e custos.

**implantacao**: Documenta a fase inicial da cultura (cultivar, espaçamento, população, data de semeadura, preparo). Base para entender efeitos de estabelecimento sobre o desempenho posterior.

**colheita / producao (se houver divisão)**: Registra dados operacionais de colheita e produtividade. Em conjunto com campo_de_producao, permite fechar o ciclo do talhão do estabelecimento à entrega, além de suportar auditorias de produtividade.

**fornecedor**: Cadastro de fornecedores de insumos/produtos (fabricantes, distribuidores). Útil para cruzar origem de insumos com desempenho, custos e aderência a recomendações.

**pessoa / usuario / conta (User/Account Management)**: Cadastro de pessoas e usuários do sistema, perfis e vínculos com inscrições. Sustenta a gestão de acesso, rastreabilidade e relacionamento produtor–consultor–organização.

**estado / regiao / localizacao (Geografia)**: Estruturas para estados e regiões, possivelmente com suporte a coordenadas/endereços. Permitem análises espaciais, agregações regionais e estratificações por ambiente.

**auditoria / log (Audit/Logging)**: Registros de ações no sistema e mudanças de estado. Importantes para rastreabilidade de processos (ex.: validação de dados, mudanças em inscrições, conferência de medições).

**equipamento (se presente)**: Referências a equipamentos de medição/aplicação. Observação: alguns IDs associados parecem não utilizados em campo_de_producao, indicando lacunas de preenchimento ou funcionalidades pouco adotadas.

**sistema / metadados (se presentes)**: Tabelas auxiliares de status, tipos, catálogos e parâmetros do sistema. Suportam padronização de processos e validações.


> De 2021 a 2024, o volume e a granularidade crescem: inscrição_desafio (7.700+ registros) continua sendo o elo entre produtor, safra, categoria e etapas de campo. O campo_de_producao detalha métricas como estande, altura de plantas, vagens por planta e coordenadas, embora revele necessidade de limpeza (outliers e unidades discrepantes). As tabelas de implantação, adubação e aplicação_agroquímico mantêm o fluxo de práticas agrícolas, agora com riqueza extra de timestamps e estágios fenológicos. Colheita (ou produção, em alguns casos) fecha o ciclo, com auditoria documentada em log/auditoria para dar confiança aos números. Tabelas de fornecedor, equipamento e metadados enriquecem o contexto de custos, origem de insumos e parâmetros do sistema.

## Codeetech Safras 2016 a 2022

O conjunto de dados de "Codeetech Safras 2016 a 2022" contém algumas informações detalhadas sobre as safras de soja no Brasil, coletadas no âmbito do desafio de produtividade do CESB entre 2016 e 2022. As tabelas representam diferentes aspectos entre os diferentes módulos - tópico apresentado no Workshop com o parceiro - do processo agrícola e da participação no desafio:

**inscricao**: Tabela central que registra cada participação no desafio, vinculando informações sobre o produtor, consultor, propriedade e a safra do desafio.

**propriedade**: Contém dados descritivos das propriedades rurais, como tamanho, área cultivada com soja, localização geográfica (cidade, estado, região).

**colheita**: Inclui os resultados de produtividade (media_produtividade_atual, media_produtividade_retrasada, media_produtividade_passada) e informações sobre o ciclo da cultivar (ciclo_de_maturacao_cultivar).

**adubacao**: Detalha as práticas de adubação, incluindo tipo, nutrientes, produtos utilizados (nome comercial, fabricante), dose e método de aplicação.

**agroquimico_aplicacao**: Fornece registros sobre a aplicação de agroquímicos, especificando o produto, estágio da cultura, forma de aplicação e dose.

**implantacao**: Descreve o processo de plantio, com foco na cultivar (idcultivar), qualidade da semente (tamanho, vigor, germinação) e detalhes do maquinário.

**historico_gleba_safra**: Apresenta o histórico de cultivos anteriores na área (gleba), permitindo a análise de rotação e sucessão de culturas.

**sistema_producao_gleba**: Informa sobre o sistema de plantio (sistema_plantio_adotado) e o tempo de exploração agrícola da área.

A interconexão dessas tabelas ocorre por meio de IDs comuns (idinscricao, idpropriedade, etc.), permitindo a realização de análises para identificar fatores que influenciam a produtividade da soja.

> O repositório Codeetech agrega, de 2016 a 2022, registros de inscrição (participações), propriedade (tamanho, área de soja, localização), histórico_gleba_safra (rotação de culturas) e sistema_producao_gleba (plantio direto, convencional). A implantação, a adubação e a aplicação_agroquímico trazem detalhes de semente, dose, método e estágio. Em colheita, temos médias de produtividade atual e histórica para cada talhão. IDs comuns conectam tudo, permitindo traçar a jornada completa de cada área ao longo dos anos.

# Conclusão Geral e Caminho para um BI

Integrar esses três blocos num repositório único nos permite criar um cubo OLAP em que dimensões como safra, localização, cultivar e sistema de produção se combinam com fatos de produtividade, custos e métricas de campo. Ao enriquecer esse modelo com atributos geográficos, temporais e de manejo, habilitamos análises rápidas e segmentadas que, em dashboards interativos, revelam retornos marginais de insumos, padrões de rotação e indicadores de sustentabilidade. Com isso, as decisões sobre cultivares, doses de fertilizante e práticas de plantio passam a se apoiar em evidências históricas, reduzimos riscos ao antecipar problemas de solo e variabilidade e fomentamos um processo contínuo de benchmarking entre produtores e consultores.


## Tabela de Narrativas Prioritárias

| Título da História                                           | Insight Estratégico                                                      | Visualização Sugerida                         | Ação ou Decisão Apoiada                                    |
| ------------------------------------------------------------ | ------------------------------------------------------------------------ | --------------------------------------------- | ---------------------------------------------------------- |
| Do plantio à colheita: o papel da implantação no rendimento  | Datas e espaçamentos ótimos podem elevar produtividade em até X %.       | Scatter plot (dias semeadura × produtividade) | Ajustar calendário de semeadura para safras futuras        |
| Nutrição vs. produtividade: ponto de saturação de adubo      | Existe dose ótima de NPK que maximiza retorno, evitando desperdício.     | Linha de tendência (dose de NPK × rendimento) | Revisar recomendações de fertilização para safra atual     |
| Auditoria e confiança: validade dos números de produtividade | Safras auditadas apresentam 8 % a mais de aderência em contratos futuros | KPI dashboard (auditadas vs. não auditadas)   | Implantar auditoria em 100 % dos talhões do próximo ano    |
| Rotações que pagam: sucessão de culturas na soja             | Áreas com rotação apresentam em média +10 % de produtividade             | Mapa de calor por gleba e produtividade       | Incentivar rotação de culturas em 70 % das propriedades    |
| Custo-benefício de insumos: fornecedores top performers      | Identificar fornecedores com melhor performance-custo por kg produzido   | Gráfico de barras (custo/kg por fornecedor)   | Negociar contratos de compra com fornecedores selecionados |
