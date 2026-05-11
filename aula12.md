# No MySQL WorkBench
1) ativar MySQL server
2) no mW, na área de scripts SQL: shell
   - rodar o 1° script (bd)
   - rodar o 2° script (inserts)
### Questão 01
```
SET FOREIGN_KEY_CHECKS = 0; -- Desativa travas de segurança
TRUNCATE TABLE Empregado;
SET FOREIGN_KEY_CHECKS = 1; -- Reativa


-- criação das tabelas 
CREATE SCHEMA IF NOT EXISTS `mydb` DEFAULT CHARACTER SET utf8 ;
USE `mydb` ;

CREATE TABLE IF NOT EXISTS `mydb`.`Departamento` (
  `idDepartamento` INT NOT NULL,
  `nome` VARCHAR(45) NOT NULL,
  `localizacao` VARCHAR(45) NOT NULL,
  `orcamento` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`idDepartamento`))
ENGINE = InnoDB;

CREATE TABLE IF NOT EXISTS `mydb`.`Empregado` (
  `idEmpregado` INT NOT NULL,
  `nome` VARCHAR(45) NOT NULL,
  `idGerente` INT NULL,
  `funcao` VARCHAR(45) NULL,
  `Departamento_idDepartamento` INT NOT NULL,
  `dataAdmissao` DATE NOT NULL,
  `salario` INT NULL,
  `comissao` INT NULL,
  PRIMARY KEY (`idEmpregado`, `Departamento_idDepartamento`),
  INDEX `fk_Empregado_Departamento_idx` (`Departamento_idDepartamento` ASC),
  CONSTRAINT `fk_Empregado_Departamento`
    FOREIGN KEY (`Departamento_idDepartamento`)
    REFERENCES `mydb`.`Departamento` (`idDepartamento`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;
--

-- inserção dos valores
INSERT INTO Departamento VALUES("1","Banco de Dados","Porto Alegre","2346");
INSERT INTO Departamento VALUES("2","Balconistas","Pelotas","10000");
INSERT INTO Departamento VALUES("3","Inteligência Artific","Pelotas","333");
INSERT INTO Departamento VALUES("4","Compiladores","Novo Hamburgo","5050");
INSERT INTO Departamento VALUES("5","Redes","Taquara","12122");

INSERT INTO Empregado VALUES("1","Mariewa",NULL,"Gerente","1","2000-04-05","2300","0");
INSERT INTO Empregado VALUES("2","Zico","1","Operário","1","1999-08-13","100","0");
INSERT INTO Empregado VALUES("3","Lula",NULL,"Presidente","5","1950-01-01","10000","0");
INSERT INTO Empregado VALUES("4","Vera Fixer","5","Balconista","2","1999-05-05","3300","0");
INSERT INTO Empregado VALUES("5","Luana Pyovany",NULL,"Gerente","2","1998-06-23","2300","0");
INSERT INTO Empregado VALUES("6","Daniela Schicarelli",NULL,"Gerente","3","1999-10-10","2300","0");
INSERT INTO Empregado VALUES("7","Luize Altenhofen",NULL,"Gerente","4","1999-04-26","2300","0");
INSERT INTO Empregado VALUES("8","Helo Pinheiro",NULL,"Gerente","5","1997-09-25","2300","0");
INSERT INTO Empregado VALUES("9","Pelé","1","Operário","1","2000-09-09","100",NULL);
INSERT INTO Empregado VALUES("10","Romário","1","Operário","5","2001-12-25","100","0");
INSERT INTO Empregado VALUES("11","Malu Mader","5","Balconista","2","2001-10-20","3400","0");
INSERT INTO Empregado VALUES("12","Antônio Fagundes","7","Vendedor","3","2002-12-22","5000","10");
--

-- seleção das colunas da tabela departamentos 
SELECT  *  FROM  Departamento;

SELECT  Empregado.nome, Empregado.funcao
FROM  Empregado
WHERE  Empregado.Departamento_idDepartamento > 3;

SELECT  Empregado.nome, Empregado.funcao
FROM  Empregado
WHERE Empregado.funcao = 'GERENTE';


-- departamentos com orçamento mensal maior que 10000
select Departamento.nome, Departamento.orcamento * 12
from Departamento
where Departamento.orcamento >= 10000;


-- apresentação da instrução anterior com orçamento mensal maior que 5000
SELECT  Departamento.nome "DEPARTAMENTO", Departamento.orcamento * 12 "ORCAMENTO ANUAL"
FROM  Departamento
WHERE Departamento.orcamento > 5000;

-- cargos existentes na empresa com o orçamento maior que 10000
select distinct Empregado.funcao
from Empregado;

-- cargos > 10000 classificados em ordem alfabetica crescente
select Empregado.nome "Nome do Empregado", Empregado.funcao "Cargo"
from Empregado
order by  Empregado.nome;

-- cargos > 10000 classificados em ordem alfabetica decrescente
select Empregado.nome "Nome do Empregado", Empregado.funcao "Cargo"
from Empregado
order by  Empregado.nome desc;

-- funcionarios que ganham entre 20 e 30 reais 
SELECT  Empregado.nome, Empregado.salario
FROM  Empregado
WHERE  Empregado.salario BETWEEN  20  AND  30;

-- dos que ganham mais de 10000, mostrar se há algum nos departamentos de 3 até 5 
SELECT  Empregado.nome,  Empregado.Departamento_idDepartamento
FROM  Empregado
WHERE  Empregado.Departamento_idDepartamento  IN  (3,5);

-- funcionarios que começam com L e recebem mais que 10000
SELECT  Empregado.nome, Empregado.funcao
FROM  Empregado
WHERE   Empregado.nome  LIKE  'L%';

-- quem não tem valor de comissão
SELECT Empregado.nome, Empregado.funcao
FROM  Empregado
WHERE  Empregado.comissao  IS  NULL;

-- quem não ganha entre 1000 e 3500
SELECT Empregado.nome,  Empregado.salario
FROM  Empregado
WHERE  Empregado.salario  NOT  BETWEEN  1000  AND  3500;

-- balconista que ganha entre 3400 e 5000
SELECT Empregado.nome, Empregado.salario, Empregado.funcao
FROM  Empregado
WHERE  Empregado.salario  BETWEEN  3400 AND 5000
AND  Empregado.funcao =  'balconista';

-- balconista ou funcionario que ganha entre 3400 e 5000
SELECT Empregado.nome, Empregado.salario, Empregado.funcao
FROM  Empregado
WHERE Empregado.salario  BETWEEN  3400 AND 5000
OR  Empregado.funcao =  'balconista';

-- coloca todas as letras em minusculo
SELECT LOWER( Empregado.nome )
FROM Empregado;

-- printa so os primeiros 5 caracteres do nome
SELECT SUBSTRING(Empregado.nome,1,5) FROM Empregado;

-- calculo da média aritmética das comissoes
SELECT  AVG(Empregado.comissao)  FROM  Empregado;

-- comissao minima
SELECT  MIN(Empregado.comissao)  FROM  Empregado;

-- comissao máxima
SELECT  MAX(Empregado.comissao)  FROM Empregado;

-- soma de todas as comissões 
SELECT  SUM(Empregado.comissao) FROM  Empregado;

-- calculo da média de comissão para cada departamento 
SELECT Empregado.Departamento_idDepartamento, AVG(Empregado.comissao)
FROM Empregado
GROUP BY Empregado.Departamento_idDepartamento;

-- media de comissoes de departamentos com mais de 2 funcionarios
SELECT  Empregado.Departamento_idDepartamento, AVG(Empregado.comissao)
FROM  Empregado
GROUP BY Empregado.Departamento_idDepartamento
HAVING COUNT(*) > 2;

-- join: mostra o nome do departamento de cada pessoa e sua funcao
SELECT A.nome, A.funcao, B.nome
FROM Empregado A, Departamento B
WHERE A.Departamento_idDepartamento = B.idDepartamento;

-- mostra o nome de cada funcionario e o nome do seu gerente 
SELECT  A.idEmpregado, A.nome, A.funcao, B.nome "CHEFE"
FROM  Empregado A, Empregado B
WHERE  A.idGerente  = B.idEmpregado;

-- cadastro de novo departamento
INSERT INTO Departamento (idDepartamento, nome, localizacao, orcamento) 
VALUES (70, "PRODUCAO", "RIO DE JANEIRO", "5000");

-- desativa o modo seguro
SET SQL_SAFE_UPDATES = 0;

-- aumenta em 20% todos os salarios menores que 1000
UPDATE Empregado 
SET salario = salario * 1.2 
WHERE salario < 1000;

-- deletou todos os funcionarios que que recebem mais de 5000
DELETE FROM Empregado WHERE Empregado.salario > 5000;

-- litsa nome e funcao de quem tem orçamento exatamente igual a 10000
SELECT  A.nome, A.funcao
FROM Empregado A
WHERE  10000 IN (SELECT Departamento.orcamento
                  FROM Departamento
                  WHERE Departamento.idDepartamento = A.Departamento_idDepartamento);
 
-- departamentos que poussuem ao menos um funcionario que ganhe mais que 3000 
SELECT A.nome
FROM Departamento A
WHERE EXISTS (SELECT * FROM Empregado
              WHERE Empregado.salario > 3000 AND Empregado.Departamento_idDepartamento = A.idDepartamento);

-- cria uma tabela virtual
CREATE VIEW EMP_DEP
AS SELECT E.nome Empregado, D.nome Departamento
FROM Empregado E, Departamento D
WHERE E.Departamento_idDepartamento = D.idDepartamento

```
