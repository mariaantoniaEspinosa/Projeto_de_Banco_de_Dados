# MySQL 
```
select Atleta.nome, Modalidade.descricao
from Atleta, Modalidade, AtletaModalidade
where Atleta.idAtleta == AtletaModalidade.atleta and
      Modalidade.idModalidade == AtletaModalidade.modalidade;
```
<img width="700" height="423" alt="{A391D471-681C-4234-80FD-499C916AEE1C}" src="https://github.com/user-attachments/assets/72e9437a-d19e-4160-9f80-c6ad80605641" />

### Atividade de Sala de Aula

```
show databases;
use mydb;

show tables;

select *
from atleta;

insert into atleta values (1, "Maria");
insert into atleta values (2, "Pedro");
insert into atleta values (3, "Yasmin");
insert into atleta values (4, "Rafael");
insert into atleta values (5, "Daniel");

select *
from modalidade;

insert into modalidade values (500, "Beach Tenis");
insert into modalidade values (501, "Padel");
insert into modalidade values (502, "Volei de Areia");

select * 
from clube;

insert into clube values (100, "Star Padel");
insert into clube values (101, "Fair Play");
insert into clube values (102, "Elite");
insert into clube values (103, "8000 sports");
insert into clube values (104, "Pier Beach Tennis");

select *
from treinador;

insert into treinador values (1000, "Lucas", 100);
insert into treinador values (1001, "Pato", 102);
insert into treinador values (1002, "Jader", 103);
insert into treinador values (1003, "Enrico", 104);

select *
from treinadormodalidade;

insert into treinadormodalidade values (1002, 500);
insert into treinadormodalidade values (1003, 500);
insert into treinadormodalidade values (1000, 501);
insert into treinadormodalidade values (1001, 501);

select *
from atletamodalidade;

insert into atletamodalidade values (1, 500);
insert into atletamodalidade values (1, 501);
insert into atletamodalidade values (2, 500);
insert into atletamodalidade values (3, 502);
insert into atletamodalidade values (4, 502);

select *
from modalidadeclube;

insert into modalidadeclube values (500, 100);
insert into modalidadeclube values (500, 101);
insert into modalidadeclube values (500, 103);
insert into modalidadeclube values (500, 104);
insert into modalidadeclube values (501, 100);
insert into modalidadeclube values (501, 101);
insert into modalidadeclube values (501, 102);

-- Quais os atletas que não praticam nenhuma modalidade?
select *
from Atleta
where idAtleta not in (select idAtleta from AtletaModalidade);

-- Qual o clube que está sem treinador?
select *
from clube
where idClube not in (select clube from Treinador);

-- Quais as modalidades que a Maria pratica?
select descricao
from Modalidade
where idModalidade in(
	select modalidade
    from AtletaModalidade
    where atleta = (select idAtleta from Atleta where nome = "Maria")
);

-- Mostre todos os atletas (nomes) e suas modalidades praticadas
select 
	(select nome from Atleta where Atleta.idAtleta = AtletaModalidade.atleta) as Nome_Atleta,
    (select descricao from modalidade where Modalidade.idModalidade = AtletaModalidade.modalidade) as Modalidade
   from AtletaModalidade; 



```
