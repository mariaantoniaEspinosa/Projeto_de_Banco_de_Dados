# Revisão para prova 
## Prova: 13/04
Modelagem de Banco de Dados Relacional

- Modelo conceitual: só entidades, atributos (chave primária) e relacionamentos
- modelo abstrato que representa a idea e é livre de tecnologia
- chave primária: pode ser um ou mais atributos que garantem unicidade na tabela/entidade
   - usado para ser apresentado ao cliente
   - por exemplo, um atributo 'nome do cliente' na entidade cliente
- Modelo lógico: transcrição das entidades em tabelas, nome de atributos mais relacionados com nomes de atributos no contexto de programação
   - destaca as chaves estrangeiras 
     - é um atributo de uma tabela que visita outra tabela
       - para ser chave estrangeira, na tablea de origem ela precisa ser chave primária
        - por exemplo, atributo transcrito do conceitual para o lógico  
            - tabela Cliente e atributo nomeCliente
        - é em geral um texto
        Aluno(codAluno, nome, matricula, cpf).
            codAluno chave primária
        Curso(codCurso, nome, area).
            codCurso chave primária
        Disciplina(codDisciplina, nome, sigla).
            codDisciplina chave primária
        Turma(codDisciplina, codCurso, ano, semestre, codAluno).
            codDisciplina, codCurso, ano e semestre formam a chave primária
            codAluno referencia Aluno
            codCurso referencia Curso
            codDisciplina referencia Disciplina

- Modelo físico: é o modelo pensando em tecnologia ou linguagem SQL
 - tipos dos atributos
  - se há atributos não nulos ou em branco

- Conceitos:
 - Entidade ou tabela
 - Atributo: chaves primárias e estrangeiras
 - Relacionamento:
            - associação
            - agregação/composição: todo e parte de (entidades fracas)
            - herança: é um tipo de
- Cardinalidade: indica a quantidade de relação de objetos de uma tabela com outra 
            1:1 -> a chave estrangeira pode ficar em qualquer uma das tabelas.
            1:n -> a chave estrangeira fica do lado do n
            n:n -> uma terceira tabela é criada contendo duas chaves estrangeiras (uma de cada tabela)   
 - substantivo que categorize/classifique algo vira entidade
 - substantivo que qualifique algo vira atributo
 -  - verbo ou as expressões 'é um tipo de', 'é parte de', 'tem relação com' viram relacionamentos
- Relacionamento Terciário: relacionamento que envolve 3 entidades
 - sugestão é converter esse relacionamento em relacionamento de 4 entidades, em que a quarta entidade substitui o relacionamento

  # Cardinalidade
Cardinalidade n:n

Engenheiro(codEngenheiro, nome).    
    codEngenheiro chave primária

Projeto(codProjeto, titulo). 
    codProjeto chave primária

Atuacao(codEngenheiro, codProjeto, funcao).
    codEngenheiro e codProjeto formam chave primária
    codEngenheiro referencia Engenheiro
    codProjeto referencia Projeto    


Medico(codMedico, nome). 
    codMedico chave primária

Paciente(codPaciente, nome).
    codPaciente chave primaria

Consulta(codMedico, codPaciente, data, hora).
    codMedico, codPaciente, data e hora formam chave primária
    codMedico referencia Medico
    codPaciente referencia Paciente

Cardinalidade 1:n

Curso(codCurso, nome).  
    codCurso chave primária

Aluno(codAluno, nome, codCurso).
    codAluno chave primária
    codCurso referencia Curso


Financeira(codFinanceira,nome).
    codFinanceira chave primária

Venda(codVenda, codFinanceira, numeroParcelas, taxaJuro).
    codVenda chave primária
    codFinanceira referencia Financeira


Grupo(codGrupo, Nome). 
    codGrupo chave primária

Empresa(numeroEmpresa, codGrupo).    
    numeroEmpresa chave primaria
    codGrupo referencia Grupo

Filial(numeroFilial, codEmpresa).
    numeroFilial chave primaria
    codEmpresa referencia Empresa
# Restrições
Restrições em Banco de Dados
    - modelagem

Restrição? 
    é algo impeditivo!
- estrutural 
- de atributo
-  SGBD pode resolver
- funcional 
- de método -> camanda de controle (programa)
-  ...
- no universo de banco de dados há outras restrições    
 - integridade -> chave primária (pode ser um atributo, mas podem ser n atributos)
   - chave primária deve garantir:
       - unicidade na tabela
          - referencial - como chave estrangeira em outra tabela
            tabela Origem (chave primária) -----> tabela Destino (chave estrangeira, contudo esta chave estrangeira
            não precisa ser chave primária na tabela Destino)
                    
- chave primária = primary key (pk)
- chave estrangeira = foreign key (fk)

Exemplo

Paciente n ---- n Medico

Paciente(codPaciente, nome). 
    codPacidente é chave primária

Medico(codMedico, nome).
    codMedico é chave primária 

Consulta(codPaciente, codMedico, data). 
    codPaciente, codMedico e data formam a chave primária

Restrições:
    - hard constraints: restrições fortes == estruturais

    - soft constraints: restrições brandas == funcionais


Inteligência Artificial:
    - Complexidade == esforço 
        - diretamente relacionada: restrições e heurísticas
        - como programador, tratar restrições e criar heurísticas pode ser
          atividades alta complexidade
# Transformações

Paciente(codPaciente, nome, email). 
    codPaciente e email são chave primária

Paciente(100,alex, alex@ufn.edu.br)
Paciente(101,lucas, lucas@ufn.edu.br)


Medico(codMedico, nome). 
    codMedico é chave primária

Medico(1,diego)

Consulta(codMedico, codPaciente, email, data). 

Consulta(1,100,alex@ufn.edu.br,25/04/2021). 
Consulta(1,100,alex@ufn.edu.br,23/04/2021). 
Consulta(1,100,alex@ufn.edu.br,15/04/2021). 
Consulta(1,101,lucas@ufn.edu.br,25/04/2021). 


Restrições de Integridade (garantir que não se tenha inconsistência)
    - duplicidade de dados -> chave primária e chave estrangeira (referencial)
    - campos opcionais/nulos



aluno(codigo, nome, codCurso, matricula, tipo, endereco).
aluno(100, ..., null)
aluno(101, ..., null)
aluno(102, ..., null)
aluno(103, ..., null)
aluno(104, ..., regina)

pessoa(codPessoa, tipo, nome,cpf, cnpj, descricao).
pessoa(1,fisica,alexandre,999,_,_).
pessoa(2,juridica,_,_,9888,UFN).

venda(codPessoa, numeroParcelas, data, valor).
venda(2,1,20/4/2021,1000).


sudo mysqldump usuario -psenha db_meuBanco >> arquivo.sql
