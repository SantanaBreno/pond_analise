# Brainstorm sobre os dados da CESB

Durante a análise dos dados da CESBé possível identificar que existem dados de vários periodos de anos. Embaixo, estão as tabelas identificadas como principais, suas descrições e observações sobre o formato dos dados.

## 2016 a 2018

- **inscricao:** Contém informações sobre as inscrições no desafio, incluindo dados do produtor, consultor, safra, propriedade, área, localização e categoria. Esta tabela é central, pois conecta muitas outras informações.

- **colheita:** Contém dados de colheita, como data da colheita, ciclo cultural, área colhida, peso bruto, percentual de impurezas e umidade, e produtividade. Essencial para avaliar os resultados do desafio.

- **implantacao:** Detalhes sobre a implantação da cultura, incluindo cultivar, espaçamento, população de plantas, data de semeadura, etc. Importante para entender as práticas agrícolas iniciais.

- **adubacao:** Informações sobre a adubação realizada, tipos de adubo, doses, formas de aplicação e estádios fenológicos. Crucial para analisar o manejo nutricional.

- **aplicacao_agroquimico:** Dados sobre a aplicação de agroquímicos, incluindo emergência, estádio fenológico, forma de aplicação e volume de calda. Relevante para entender o manejo fitossanitário.

agroquimico: Informações sobre os agroquímicos específicos utilizados, tipo, nome, dose, unidade e fabricante. Complementa a tabela aplicacao_agroquimico.

- **solo:** Detalhes sobre as características do solo, textura, teor de argila, classificação e histórico de correção. Fundamental para entender o ambiente de cultivo.

- **safra:** Informações sobre as safras do desafio, incluindo ano e períodos de inscrição. Essencial para contextualizar os dados por safra.
cultivar: Cadastro das cultivares utilizadas. Permite analisar o impacto da cultivar na produtividade.

- **fornecedor:** Cadastro dos fornecedores de produtos. Pode ser útil para analisar a relação entre fornecedores e práticas agrícolas/resultados.

- **pessoa:** Informações gerais sobre as pessoas envolvidas (produtores, consultores, etc.). Permite vincular dados de outras tabelas a indivíduos.

- **estado:** Cadastro dos estados brasileiros e suas regiões. Permite análises geográficas.