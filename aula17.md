```
select autor.nome 
from livro, genero, livro_autor, autor
where genero.descricao = 'Infantil' and
	  livro.idGenero = genero.idGenero and
	  livro.idLivro = livro_autor.idLivro and 
	  autor.idAutor = livro_autor.idAutor;


select autor.nome 
from livro
inner join  genero on livro.idGenero = genero.idGenero 
inner join livro_autor on livro.idLivro = livro_autor.idLivro 
inner join autor on autor.idAutor = livro_autor.idAutor
where genero.descricao = 'Infantil';

select *
from livro

SELECT l.*
FROM livro l
INNER JOIN (
    SELECT idLivro
    FROM livro_autor
    GROUP BY idLivro
    HAVING COUNT(idAutor) > 1
) sub ON l.idLivro = sub.idLivro;

SELECT DISTINCT livro.*
FROM livro
INNER JOIN livro_autor AS tabela_autor_um ON livro.idLivro = tabela_autor_um.idLivro
INNER JOIN livro_autor AS tabela_autor_dois ON livro.idLivro = tabela_autor_dois.idLivro
WHERE tabela_autor_um.idAutor <> tabela_autor_dois.idAutor;

SELECT livro.titulo, COUNT(livro_autor.idAutor) AS total_autores
FROM livro_autor, livro
WHERE livro.idLivro = livro_autor.idLivro
GROUP BY livro_autor.idLivro, livro.titulo
HAVING COUNT(livro_autor.idAutor) > 1;

select livro.titulo, count (livro_autor.idAutor) as total_autores
from livro
join livro_autor on livro.idLivro = livro_autor.idLivro
group by livro.idLivro, Livro.Titulo
having count (livro_autor.idAutor) > 1

-- DESAFIOS:

-- 1) Entender a diferença de inner join, left join e right join
-- 2) Entender a diferença de Banco de Dados Relacionais e Banco de Dados Não Relacionais 

```
