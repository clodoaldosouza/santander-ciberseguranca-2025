# 🛡️ Básico – Estrutura de Dados

---

## 📘 Descrição

Em sistemas de autenticação segura, é comum bloquear contas após múltiplas tentativas de login inválidas consecutivas.  
Esse mecanismo evita ataques de força bruta e protege a conta do usuário.

Neste desafio, você deverá verificar uma lista de tentativas de login e identificar se a conta deve ser bloqueada com base em tentativas falhas seguidas.

> Uma conta deve ser bloqueada se houver **3 ou mais tentativas consecutivas de falha**.

---

## 📥 Entrada

Uma lista com strings representando o resultado de tentativas de login.  
Cada string pode ser:

- `"sucesso"`
- `"falha"`

As tentativas são fornecidas em ordem cronológica.

---

## 📤 Saída

- `"Conta Bloqueada"`, se houver 3 ou mais falhas consecutivas  
- `"Acesso Normal"`, caso contrário

---

## 🧪 Exemplos

A tabela abaixo apresenta exemplos com alguns dados de entrada e suas respectivas saídas esperadas.  
Certifique-se de testar seu programa com esses exemplos e com outros casos possíveis.

| Entrada                          | Saída            |
|----------------------------------|------------------|
| sucesso, falha, falha, falha     | Conta Bloqueada  |
| falha, falha, sucesso, falha     | Acesso Normal    |
| falha, falha, falha, sucesso     | Conta Bloqueada  |
| sucesso, sucesso, falha, sucesso | Acesso Normal    |

⚠️ **Atenção:**  
É extremamente importante que as entradas e saídas sejam exatamente iguais às descritas na descrição do desafio de código.

---

## 💡 Observação

Os desafios apresentados aqui têm como objetivo principal exercitar os conceitos aprendidos e proporcionar um primeiro contato com lógica de programação.  
Caso não tenha experiência em programação, utilize o template disponível e preencha com os conceitos aprendidos.  
Para resetar o template, basta clicar em `Restart Code`.

---