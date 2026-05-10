 Database Cinema: Análise de Filmes e Diretores com SQL

Este projeto foi desenvolvido para para demonstrar habilidades em Modelagem de Dados, Normalização e Manipulação de Bancos de Dados Relacionais utilizando SQL (SQLite).

Contexto do Projeto:
O objetivo foi sair de uma estrutura de dados desorganizada para um modelo relacional robusto, permitindo analisar métricas cinematográficas cruzadas entre diretores e títulos. 

A escolha do SQLite se deu pela agilidade e eficiência para a criação de um banco de dados local focado em análise de performance.

Modelagem Relacional (Schema)

O banco de dados foi estruturado seguindo as regras de Normalização, separando as entidades para garantir a integridade referencial através de Chaves Estrangeiras (FK).

Estrutura da Tabela Principal (`Filmes`):

CREATE TABLE Filmes (
    id_filmes      INTEGER PRIMARY KEY,
    nome_filme     TEXT NOT NULL,
    ano_lancamento INTEGER,
    id_diretor     INTEGER,
    genero         TEXT,
    pais           TEXT,
    nota_imdb      REAL,
    nota_rotten    INTEGER,
    premios        INTEGER,
     Estabelecendo o relacionamento com a tabela de Diretores
    FOREIGN KEY (id_diretor) REFERENCES Diretores(id_diretor)
);

Exemplo de Extração de Insights Relacionais

Esta consulta realiza o cruzamento de dados (INNER JOIN) entre a tabela de fatos (Filmes) e a tabela de dimensão (Diretores) para consolidar um relatório unificado

SELECT 
    Filmes.nome_filme, 
    Diretores.nome_diretor
FROM Filmes
INNER JOIN Diretores 
    ON Filmes.id_diretor = Diretores.id_diretor;
