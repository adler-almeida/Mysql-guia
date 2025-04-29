# 🐬 Guia SQL com MySQL

> Repositório de anotações, scripts e conceitos essenciais para consulta rápida sobre SQL utilizando MySQL. Baseado no curso gratuito do [Curso em Vídeo](https://www.cursoemvideo.com) ministrado por Gustavo Guanabara.

---

## 📌 Tipos Primitivos em SQL

### 🔢 Numéricos
| Tipo | Descrição |
|------|-----------|
| Inteiros | `TINYINT`, `SMALLINT`, `INT`, `BIGINT` |
| Reais    | `DECIMAL`, `FLOAT`, `DOUBLE`, `REAL` |
| Lógicos | `BIT`, `BOOLEAN` |

### 📆 Data e Tempo
- `DATE`, `DATETIME`, `TIMESTAMP`, `TIME`, `YEAR`

### 🔤 Literais
| Tipo | Subtipos |
|------|----------|
| Caractere | `CHAR`, `VARCHAR` |
| Texto     | `TINYTEXT`, `TEXT`, `MEDIUMTEXT`, `LONGTEXT` |
| Binário   | `TINYBLOB`, `BLOB`, `MEDIUMBLOB`, `LONGBLOB` |
| Coleção  | `ENUM`, `SET` |

### 🗺️ Espaciais
- `GEOMETRY`, `POINT`, `POLYGON`, `MULTIPOLYGON`, etc.

---

## 🧱 Comandos SQL Básicos
```sql
CREATE DATABASE nome_do_banco;
DROP DATABASE nome_do_banco;
USE nome_do_banco;
```

---

## 🌍 Charset e Collation no MySQL

### ✅ O que é `DEFAULT CHARACTER SET utf8mb4`?
- Define que o banco de dados usará **UTF-8 completo**, permitindo armazenar **qualquer caractere Unicode**, inclusive **emojis**.

### 🔄 Diferença entre `utf8`, `utf8mb3` e `utf8mb4`

| Charset     | Bytes | Suporte a Emojis | Observação |
|-------------|-------|------------------|-------------|
| utf8        | 3     | Não              | Nome antigo para utf8mb3 |
| utf8mb3     | 3     | Não              | Limitado a 3 bytes |
| utf8mb4     | 4     | Sim              | UTF-8 verdadeiro (completo) |

### ✨ Collation
O `COLLATE utf8mb4_general_ci`:
- **`ci` = case insensitive**
- Ignora diferenças entre letras maiúsculas/minúsculas e acentos.

#### Exemplo prático:
```sql
SELECT * FROM pessoas WHERE nome = 'joao';
```
Vai encontrar registros como "João", "JOAO" ou "joão" se o collation for `utf8mb4_general_ci`.

#### Outras collations populares:
- `utf8mb4_unicode_ci`: considera regras linguísticas mais precisas.
- `utf8mb4_bin`: case-sensitive, compara os bits exatos.

---

## 🏗️ Criando Banco de Dados
```sql
CREATE DATABASE cadastro
  DEFAULT CHARACTER SET utf8mb4
  DEFAULT COLLATE utf8mb4_general_ci;
```

---

## 👤 Exemplo: Criando Tabela `pessoa`
```sql
CREATE TABLE pessoa (
  id INT NOT NULL AUTO_INCREMENT,
  nome VARCHAR(30) NOT NULL,
  nascimento DATE,
  sexo ENUM('M','F'),
  peso DECIMAL(5,2),
  altura DECIMAL(3,2),
  nacionalidade VARCHAR(20) DEFAULT 'Brasil',
  PRIMARY KEY (id)
);
```

### 🔎 Explicações importantes:
- `NOT NULL`: campo obrigatório (constraint).
- `ENUM('M','F')`: restringe os valores aceitos para o campo `sexo`.
- `DECIMAL(5,2)`: números com até 5 dígitos no total e 2 casas decimais.
- `DEFAULT 'Brasil'`: preenche com valor padrão se nada for informado.
- `PRIMARY KEY (id)`: identifica unicamente cada registro (tupla). Pode ser substituído por valores exclusivos como CPF, Matrícula etc.

> ✨ Dica: não precisa repetir `DEFAULT CHARSET = utf8mb4` na tabela se já foi definido no banco de dados.

---

## 📚 Fontes e Créditos
- Curso gratuito de **MySQL com SQL** pelo professor **Gustavo Guanabara**: [Curso em Vídeo](https://www.cursoemvideo.com)
- Documentação oficial do MySQL: https://dev.mysql.com/doc/

---

Se você achou este repositório útil, deixe uma estrela ⭐ e compartilhe com colegas que também estão estudando SQL e não esqueção de seguir!

> Contribuições são bem-vindas!

