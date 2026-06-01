# Correção Prova
## Atividades de Revisão
```
SELECT livro.titulo, COUNT(livro_autor.idAutor) AS total_autores
FROM livro, livro_autor
WHERE livro.idLivro = livro_autor.idLivro
GROUP BY livro.idLivro, livro.titulo
HAVING COUNT(livro_autor.idAutor) > 1;

-- quais os livros que tem mais de um autor
select idLivro as "Livros com mais de um autor"
from livro_autor
group by idLivro
having count(idAutor)>1;

select livro.titulo, autor.nome as "Autor"
from livro, autor, livro_autor
where livro.idLivro = livro_autor.idLivro and
autor.idAutor = livro_autor.idAutor and
livro.idLivro in (
    select idLivro 
    from livro_autor
    group by idLivro
    having count(idAutor) > 1
);

SELECT a.nome, l.titulo
FROM livro l
JOIN livro_autor la_principal ON l.idLivro = la_principal.idLivro
JOIN autor a ON a.idAutor = la_principal.idAutor
WHERE l.idLivro IN (
    SELECT idLivro 
    FROM livro_autor 
    GROUP BY idLivro 
    HAVING COUNT(idAutor) > 1
);
```
   
