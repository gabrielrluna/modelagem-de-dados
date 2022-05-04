# Comandos SQL para CRUD

## Resumo
- C -> Create (inserir dados)
- R -> Read (ler dados)
- U - Update (atualizar dados)
- D -> Delete (excluir dados)


## INSERT

```sql
INSERT INTO fabricantes (nome) VALUES ('Asus');
INSERT INTO fabricantes (nome) VALUES ('Dell');
INSERT INTO fabricantes (nome) VALUES ('Apple'),('LG'), ('Samsung'),('Brastemp');
```


### Produtos

```sql
INSERT INTO produtos (nome, descricao, preco, quantidade, fabricante_id) VALUES (
    'Ultrabook',
    'Ultrabook Asus com processador Intel Core i12, memória RAM de 16GB e Windows 11',
    6500.99,
    7,
    1)
```

```sql
INSERT INTO produtos (nome, descricao, preco, quantidade, fabricante_id) VALUES 
('Ultrabook',
'Refrigerador Frost-free com acesso à Internet das Coisas e blablabla',
1500,
10,
6 -- Brastemp
),

('iPhone 13 Pro Max',
'Alta durabilidade, processador Bionic 14, 128GB de armazenamento, 6GB de RAM e caro pra burro',
6999.99,
2,
3 -- Apple
),

('iPad Mini',
'Tablet Apple com tela retina display de 4k, memória interna de 64GB, acesso à iCloud.',
4999.99,
8,
3 -- Apple
),
```


## SELECT

### Ler dados da tabela produtos
```sql
SELECT * FROM produtos;
SELECT nome, preco FROM produtos;
SELECT preco, nome FROM produtos WHERE preco < 3000;
```

### Operadores Lógicos - E, OU, NÃO
```sql
SELECT * FROM produtos 
WHERE preco >= 5000 AND preco < 8000;

SELECT nome, preco FROM produtos
-- Dos fabricantes Apple ou Microsoft
WHERE fabriante_id = 3 OR fabriante_id = 8;


SELECT nome, preco, quantidade FROM produtos
WHERE NOT fabricante_id = 3

```

### Filtros
```sql
SELECT nome, preco FROM produtos ORDER BY nome; -- ascendente
SELECT nome, preco FROM produtos ORDER BY nome DESC; -- descendente
```

```sql
SELECT nome, descricao FROM produtos;
WHERE descricao LIKE '%processador%'; -- LIKE (COMO)
-- % é um operador coringa. Significa "qualquer texto", ou melhor dizendo, pouco importa o texto
```

### Operacões e Funções de Agregação
```sql
SELECT SUM (preco) FROM produtos; -- Soma
SELECT SUM (preco) AS "Quantidade em Estoque"; -- AS é um "Aliás" (Apelido)
FROM produtos;
```

### Average - Média
```sql
SELECT AVG(preco) AS "Média dos Preços" FROM produtos;

-- ROUND = Arredondamento 
SELECT ROUND(AVG(preco),2) AS "Média dos Preços" FROM produtos;

-- COUNT = Contagem 
SELECT COUNT(id) AS "Quantidade de Produtos" FROM produtos;
SELECT COUNT(fabricante_id) AS "Quantidade de Fabricantes" FROM produtos;

-- DISTINCT é um comando para evitar a duplicidade na contagem em campos que não são chave-primária
SELECT COUNT(DISTINCT fabricante_id) AS "QTD de Fabricantes" FROM produtos;
SELECT nome, preco, quantidade, (preco*quantidade) AS Total FROM produtos;
```

### Agrupamentos

```sql
SELECT fabricante_id, SUM(preco) AS total FROM produtos GROUP BY fabricante_id;
-- GROUP BY = Segmenta o resultado da consulta. No caso, somei os preços e segmentei por cada fabricante.
```
