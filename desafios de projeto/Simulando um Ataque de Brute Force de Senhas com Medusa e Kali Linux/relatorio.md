# Relatório Técnico: Auditoria de Segurança com Kali Linux e Medusa

## 📌 Objetivo do Projeto
Simular cenários de ataque de força bruta em ambiente controlado utilizando Kali Linux e a ferramenta Medusa, explorando serviços vulneráveis como FTP, DVWA (formulário web) e SMB. O projeto visa compreender técnicas ofensivas e propor medidas defensivas eficazes.

## 🖥️ Estrutura do Ambiente
• 	VirtualBox com duas VMs:
• 	Kali Linux (atacante)
• 	Metasploitable 2 (alvo)
• 	Rede interna (Host-Only) configurada para comunicação direta entre as VMs.

## 🔧 Ferramentas Utilizadas
• 	Kali Linux (Medusa, Hydra, Nmap, Enum4linux)
• 	Metasploitable 2
• 	DVWA (Damn Vulnerable Web Application)
• 	Wordlists personalizadas
• 	Wireshark (para análise de tráfego)

## ⚔️ Cenários de Ataque
### 1. Ataque de Força Bruta em FTP
Serviço alvo: vsFTPd (porta 21)
Comando Medusa:

Wordlist:
Usuario
```
user
msfadmin
admin
root
```
Senha
```
123456
password
qwerty
msfadmin
```

Resultado: Acesso obtido com Usuario `msfadmin` e Senha `msfadmin`.
Mitigação:
• 	Desativar contas padrão
• 	Implementar bloqueio após tentativas falhas
• 	Usar autenticação multifator

### 2. Automação de Ataques em Formulário Web (DVWA)
Configuração DVWA: Security Level = Low
Ferramenta: Hydra
Comando:

Wordlist:
Usuario
```
user
msfadmin
admin
root
```
Senha
```
123456
password
qwerty
msfadmin
```

Resultado: Usuario `admin` e Senha `password` identificada com sucesso.
Mitigação:
• 	Aumentar o nível de segurança do DVWA
• 	Implementar CAPTCHA
• 	Monitorar tentativas de login

### 3. Password Spraying em SMB com Enumeração de Usuários
Ferramenta de enumeração: Enum4linux
Comando:

Usuários identificados:
• 	msfadmin
• 	user
• 	service
Ataque com Medusa:

Wordlist:
User
```
user
msfadmin
service
```
Password
```
password
123456
Welcome123
msfadmin
```

Resultado: Acesso obtido com Usuario `msfadmin` e Senha `msfadmin`.
Mitigação:
• 	Políticas de senha forte
• 	Auditoria de contas inativas
• 	Limitar tentativas de login

## 📚 Aprendizados e Reflexões
• 	A força bruta continua sendo uma técnica eficaz contra sistemas mal configurados
• 	A importância de ambientes de teste para aprendizado seguro
• 	Medusa é poderosa, mas exige precisão nos parâmetros
• 	Enumeração de usuários é etapa crítica para ataques como password spraying

## ✅ Recomendações Gerais de Segurança
• 	Implementar autenticação multifator
• 	Monitorar logs de acesso
• 	Usar senhas complexas e únicas
• 	Atualizar e endurecer serviços expostos

## 📂 Compartilhamento no GitHub
Estrutura:
```
/desafio 01
  ├─ relatorio.md
  ├─ comandos_utilizados.MD
  ├─ wordlists/
  └─ evidencias/
```
