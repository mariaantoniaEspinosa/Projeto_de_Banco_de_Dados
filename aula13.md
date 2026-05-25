# SQL - Structured Query Language
- DML
- DDL
  - select (consulta; visão; consulta de inserção, atualização, deleção)
  - insert
  - update
  - delete
    - CRUD
## BD
- Relacional
- Não Relacional - **NoSQL** -> MongoDB - FireBase
  - X
  - Meta
  - ...
## Comandos
- *select*
  - selecionando tudo de uma tabela: SELECT *;
- *from*
  - indica de qual tabela os dados estão sendo buscados: FROM clientes;
- where
  - filtra os resultados: SELECT nome, idade FROM clientes WHERE idade > 18;
- order by
  - ordena por ordem crescente ASC ou decrescente DESC os resultados da consulta: SELECT nome, idade FROM clientes ORDER BY idade;
- group by
  - SELECT departamento, AVG(salario) AS media_salario FROM funcionarios GROUP BY departamento;
  - <img width="585" height="364" alt="image" src="https://github.com/user-attachments/assets/44b9d78a-e3b3-498b-b35f-e5156ae2596e" />
  - agrupa linhas em uma coluna 
- having
  - filtro para grupos: SELECT vendedor, SUM(valor) AS total FROM vendas GROUP BY vendedor HAVING total > 200;
- as
  - organiza o resultado: SELECT SUM(valor) AS total_vendas FROM vendas;
- between and
  - filtra valores dentro de um intervalo: SELECT nome, salario FROM funcionarios WHERE salario BETWEEN 2000 AND 5000;
- in
  - verifica valores dentro de uma lista: SELECT nome, cidade FROM clientes WHERE cidade IN ('São Paulo', 'Rio de Janeiro', 'Curitiba');
- Like L%
  - busca por padrão de texto:

```
-- Começa com L
WHERE nome LIKE 'L%';
-- Lucas, Larissa, Luis, Luana...
```
- Null
  - verificar ausência de valores: WHERE email IS NULL;

Para estudar SQL: https://sqlbolt.com/
