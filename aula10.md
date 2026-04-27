<img width="881" height="513" alt="{98855F75-20EE-466E-A3F4-AF69C6401EC1}" src="https://github.com/user-attachments/assets/3c506774-2228-406b-9752-144b7818edf5" />

# 
### O que está acontecendo aqui?
    - select *  
    - from Paciente
- mostra os pacientes cadastrados
    - where sexo == 'F';
- mostra todos os pacientes do sexo feminino
    - select *
    - from Consulta
    - where id_paciente = 4
- mostra as consultas do paciente número 4 (Maria)
## 
- listar as consultas (todos os dados) de pacientes do sexo feminino
    - select Paciente.nome, Consulta.data, Medico.nome
    - from Paciente, Consulta
    - where Paciente.sexo = 'F' and Paciente.id_paciente == Consulta.id_paciente and Medico.id_medico == Consulta.id_medico (há dois joins = produto cartesiano);
- Mostrar os pacientes (nome) que tiveram ou vão ter consulta com médico traumato
    - select Paciente.nome, Consulta.data, Medico.nome
    - from Paciente, Medico, Consulta
    - where Medico.especialidade == 'Traumato' and Medico.id_medico == Consulta.id_medico and Paciente.id_paciente == Consulta.id_paciente;
- Mostrar todos os pacientes do sexo feminino que tem consulta
  - Select Consulta.data
  - from Consulta
  - where id_paciente in
    - select id_paciente
    - from Paciente
    - where sexo == 'f'
##
<img width="628" height="458" alt="{63C6486C-F3BC-47CB-9D49-AB802E482B57}" src="https://github.com/user-attachments/assets/76c7d884-fc88-4951-b929-e796f953ae37" />

- select ALuno.nome, Curso.descricao
- from Disciplina, Turma, Matricula
- where Disciplina.nome == "Estrutura de Dados" and Turma.ano_semestre like "2026%" (filtro básico) and Disciplina.id_disciplina == Turma.id_disciplina and Turma.id_turma == Matricula.id_turma and Matricula.id_aluno == ALuno.id_aluno and Aluno.id_curso == Curso.id_curso;

<img width="628" height="458" alt="image" src="https://github.com/user-attachments/assets/9a8dde01-72eb-4729-8f5b-f8b9ae7ccb50" />
### Histórico de disciplinas cursadas/cursando pelo Alexz

### MySQL
```
create schema ufn_db;
use ufn_db;
show tables;

create table curso (
	id_curso int primary key not null,
    descricao varchar (50) not null
);

select *
from curso;

create table aluno (
	id_aluno int primary key not null,
	nome varchar (50) not null,
	id_curso int,
	constraint fk_curso foreign key (id_curso) references curso(id_curso)
);

select *
from aluno;

create table Disciplina (
	id_disciplina int primary key not null,
    nome varchar (50) not null
);

select *
from Disciplina;

create table turma (
	id_turma int primary key not null,
	ano_semestre varchar (50) not null,
	id_disciplina int,
	constraint fk_disciplina foreign key (id_disciplina) references Disciplina(id_disciplina)
);

select *
from turma;

create table Matricula (
	id_matricula int primary key not null,
    id_aluno int,
    constraint fk_aluno foreign key (id_aluno) references aluno(id_aluno),
    id_turma int,
    constraint fk_turma foreign key (id_turma) references turma(id_turma)
);

select *
from matricula;
```
