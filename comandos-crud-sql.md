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
```
