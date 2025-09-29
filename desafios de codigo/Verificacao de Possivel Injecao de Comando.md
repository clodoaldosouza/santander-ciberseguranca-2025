# 🛡️ Básico – Estrutura de Dados

---

## 📘 Descrição

Em cibersegurança, é fundamental monitorar a entrada de dados fornecidos pelo usuário para prevenir **injeção de comandos**.  
Comandos maliciosos podem ser executados no sistema, comprometendo sua segurança.

Neste desafio, você deve criar uma lógica para identificar se um comando fornecido pelo usuário contém caracteres que possam ser usados para realizar **injeções de comandos**.

---

## 🎯 Objetivo

Identificar se o comando fornecido contém caracteres frequentemente utilizados para executar múltiplos comandos de forma encadeada ou maliciosa, como `;`, `&`, `|` e `$`.

### Regras de detecção:

- O comando será considerado suspeito se contiver qualquer um dos seguintes caracteres: `;`, `&`, `|`, ou `$`.
- Se o comando contiver qualquer um desses caracteres, será considerado **suspeito** e o sistema deve alertar sobre um possível risco de **injeção de comando**.

---

## 📥 Entrada

A entrada será composta por uma string representando o comando fornecido pelo usuário.

- **Comando:** uma string contendo o comando a ser analisado.

---

## 📤 Saída

A saída deve retornar:

- `"Comando Suspeito"` se o comando contiver qualquer um dos caracteres mencionados.
- `"Comando Seguro"` caso contrário.

---

## 🧪 Exemplos

A tabela abaixo apresenta exemplos com alguns dados de entrada e suas respectivas saídas esperadas.  
Certifique-se de testar seu programa com esses exemplos e com outros casos possíveis.

| Entrada                  | Saída             |
|--------------------------|-------------------|
| ls -la                   | Comando Seguro    |
| rm -rf /                 | Comando Seguro    |
| cat file.txt; rm -rf /   | Comando Suspeito  |
| echo $PATH               | Comando Suspeito  |
| whoami && ls            | Comando Suspeito  |
| pwd                      | Comando Seguro    |

⚠️ **Atenção:**  
É extremamente importante que as entradas e saídas sejam exatamente iguais às descritas na descrição do desafio de código.

---

## 💡 Observação

Os desafios apresentados aqui têm como objetivo principal exercitar os conceitos aprendidos e proporcionar um primeiro contato com lógica de programação.  
Caso não tenha experiência em programação, utilize o template disponível e preencha com os conceitos aprendidos.  
Para resetar o template, basta clicar em `Restart Code`.

---