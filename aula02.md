# Aula 02 
## Engenharia de software 
- análise de requisitos (exigências, fundamentos, obrigações);
- modelagem;
- projeto;
- implementação;
- testes/validação;
- entrega;
## Projeto de banco de dados = etapadas de análise e modelagem
- Modelagem: esquemas visuais -> artefatos -> diagramas
  - Três fases/níveis:
    - conceitual: cliente
    - lógica: programador
    - física: arquitetura de software
## Modelagem conceitual/Nível 1
- abstrata/cliente
  - Mapear:
    - Entidades -> classes -> tabelas;
    - Atributos -> variáveis -> colunas;
      - Atributos identificadores = chaves primárias = não ter repetição no banco/erro;
    - Relacionamentos -> relação de um objeto de uma tabela com outro(os) de outra tabela;
      - Cardinalidade - > cliente que fornece conforme restrições; mínimo e máximo entre entidades de um relacionamento;
- Exemplo:
  - Cliente; -> primeria Entidade;
  - Nome; **CPF**; E-mail; Endereço; -> Atributos;
  - Categoria; -> segunda Entidade;
  - Nome; **idCategoria**; -> Atributos;
  - Relacionamento -> Cliente + Categoria; Cliente TEM QUE TER no mínimo 1 categoria e no máximo N categorias;
## Banco de Dados: coleção de diretórios ou pastas; MySQL; SQL Server;
- Conjunto de tabelas, colunas e relações;
- SGBD (sistema gerenciador de banco de dados) = serviços sobre o banco de dados;
  - Segurança;
  - Manipulação;



