# Lab: Implementação de Acesso Remoto Seguro (SSH vs Telnet) 🔒🌐

## 📌 Contexto do Projeto
Este repositório contém a resolução de um laboratório prático do curso de **Fundamentos de Redes da Cisco**, realizado no simulador **Cisco Packet Tracer**. O foco principal foi configurar e validar o acesso remoto a dispositivos de rede, comparando a insegurança do protocolo Telnet com a robustez do SSH.

No cenário proposto, uma topologia composta por um roteador central (**HQ**) e terminais de usuário (**PC0** e **PC1**) foi utilizada para testar a comunicação e o gerenciamento remoto.

## 🛠️ Objetivos Técnicos
* **Verificar Conectividade:** Validar se os hosts finais receberam endereçamento via DHCP e possuem comunicação ICMP (Ping) com o roteador.
* **Acesso Remoto Inseguro:** Demonstrar a tentativa de acesso via Telnet e entender por que conexões não criptografadas são rejeitadas por padrão em dispositivos configurados corretamente.
* **Acesso Remoto Seguro:** Estabelecer uma sessão SSH bem-sucedida com privilégios de administrador para gerenciamento do roteador.

## 🚀 Passo a Passo Realizado

### 1. Validação de IP e Conectividade
* **Comando utilizado:** `ipconfig` no terminal do PC.
* **Resultado:** Verificou-se que o PC obteve um endereço IP dinâmico através do servidor DHCP da rede.
* **Teste de comunicação:** Execução de `ping 64.100.1.1` (Interface G0/0/1 do roteador HQ).

### 2. Tentativa de Conexão via Telnet
* **Comando:** `telnet 64.100.1.1`.
* **Saída observada:** `[Connection to 64.100.1.1 closed by foreign host]`.
* **Análise:** O dispositivo remoto recusou a conexão porque não está configurado para aceitar tráfego Telnet (porta 23), que é inerentemente vulnerável.

### 3. Acesso Bem-Sucedido via SSH
* **Comando:** `ssh -l admin 64.100.1.1`.
* **Autenticação:** Utilizado usuário `admin` e senha `class`.
* **Resultado:** Acesso concedido com sucesso, chegando ao prompt de privilégio `HQ#`.

## 🛡️ Visão de Cibersegurança e Perícia Digital

### Impacto na Segurança
O uso do SSH em vez do Telnet é uma medida de **Hardening** indispensável. O Telnet transmite dados em texto claro, permitindo que ataques de interceptação (*Sniffing*) exponham credenciais críticas. O SSH utiliza criptografia para garantir a **Confidencialidade** e **Integridade** dos comandos administrativos.

### Contexto Forense e Investigação
* **Perícia:** Em uma análise forense, a presença de sessões Telnet facilita a reconstrução completa dos comandos de um invasor através da captura de pacotes. No SSH, a análise foca em logs de autenticação e tentativas de força bruta, já que o conteúdo da sessão permanece cifrado.
* **Cena do Crime Digital:** Um perito digital verificará as listas de controle de acesso (ACLs) do roteador para entender se o acesso não seguro foi uma falha de configuração que permitiu o comprometimento da rede.

## 📁 Arquivos no Repositório
* `Laboratorio_SSH_Telnet.pkt`: Arquivo do Cisco Packet Tracer com a topologia configurada.
* `screenshots/`: Pasta contendo capturas de tela das etapas de comando e login.

---
**Curso:** Fundamentos de Redes - Cisco Networking Academy
**Ferramenta:** Cisco Packet Tracer
