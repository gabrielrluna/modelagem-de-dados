# Comandos SQL - Referência

## Modelagem Física

### Criar Banco de Dados

``` sql
CREATE DATABASE vendas CHARACTER SET utf8mb4;
```

### Criar tabela Fabricantes
```sql
CREATE TABLE fabricantes(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL
)
```

### Visualizar detalhes estruturais da tabela
```sql
DESC fabricantes;
```


### Criar tabela produtos

```sql
CREATE TABLE produtos(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(45) NOT NULL,
    preco DECIMAL(6,2) NOT NULL
    fabricante_id INT NOT NULL
);
```


### Criação da chave estrangeira (relacionamento entre tabelas)

```sql
ALTER TABLE produtos
    ADD CONSTRAINT fk_produtos_fabricantes

    FOREIGN KEY (fabricante_id) REFERENCES fabricantes(id)
```

#CONSTRAINT é uma restrição definida no relacionamento
#A chave estrangeira deve fazer referência à chave primária 

### Adicionar campo/coluna em uma tabela

```sql
ALTER TABLE produtos ADD fabricante_id INT NOT NULL AFTER preco;
```

add - Adiciona
remove - remove
