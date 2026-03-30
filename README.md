# monitorchina
## Resumo
O *Monitor China* é uma iniciativa de extensão universitária voltada ao acompanhamento sistemático e à análise de sentimentos expressos em redes sociais digitais sobre a China contemporânea, a partir de postagens em *língua portuguesa*. Com as análises produzidas por meio deste projeto, buscamos contribuir para os estudos de opinião pública no Brasil, com foco nas percepções sociais sobre temas internacionais, política externa, economia, cultura e relações Brasil–China. O foco inicial é o Twitter (X), onde serão feitas análises mensais acerca de tweets que fazem menção à China.

## Tecnologias utilizadas
<div>
<img align="center" alt="Octoparse" height="50" width="50" src="https://static.macupdate.com/products/62581/l/octoparse-logo.png?v=1593495743">
<img align="center" alt="Python" height="50" width="60" src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg">
<img align="center" alt="SQL Server" height="40" width="50" src="https://github.com/devicons/devicon/blob/v2.17.0/icons/microsoftsqlserver/microsoftsqlserver-original.svg">
</div>

## Arquitetura Lógica
Neste repositório, as pastas estão organizadas de forma que sejam separados os dados do processamento. 
### Dados
Em termos de dados, eles foram dividos utilizando a arquitetura medalhão, metodologia proposta por uma das principais ferramentas para armazenamento e processamento de dados: Databricks. Neste padrão de desenvolvimento, os dados são divididos em *bronze*, *silver* e *gold*.
- *Bronze*: a camada bronze é onde fica armazenado o dado bruto, tal qual é extraído da origem. Ele serve para guardar o histórico, como uma fonte da verdade, e permite que o reprocessamento seja possível, caso necessário.
- *Silver*: a camada silver é onde fica armazenado o dado refinado para uso geral. Em termos práticos, significa que ele passou por transformações mínimas para garantir a qualidade, como a renomeação de colunas, exclusão de linhas duplicadas, ajustes de formatação para legibilidade, etc.
- *Gold*: a camada gold é onde fica armazenado o dado orientado a um contexto. Aqui ele foi modelado para a necessidade de negócio, que geralmente incluem agregações, criação de campos customizados, eliminação de colunas desnecessárias para a iniciativa em questão, inclusão de filtros, etc.

Ademais, os dados de identificação dos autores também foram anonimizados a fim de preservar as diretrizes da plataforma.

### Scripts
Em termos de scripts, eles foram divididos em transformação de dados, onde o foco foi o desenvolvimento em SQL para gerar a arquitetura de camadas de dados, e a análise propriamente dita, onde o foco foi utilizar Python para a realização de análise exploratória do dado, bem como a transformação necessária para o uso de bibliotecas de análises de texto que gerarão as classificações de sentimento.

