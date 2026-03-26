🛡️ Projeto Prático: Auditoria de Autenticação com Medusa e Kali Linux

Este repositório contém a documentação e os artefatos de um laboratório prático focado em ataques de força bruta (Brute Force) e medidas de mitigação, desenvolvido para a formação em Cybersecurity da DIO.

📑 Objetivo

O objetivo deste projeto é simular cenários reais de tentativas de invasão por dicionário e força bruta em serviços de rede (como FTP e SMB) utilizando o Kali Linux e a ferramenta Medusa. O foco principal é validar a robustez de políticas de senhas e entender como proteger infraestruturas contra esse tipo de vetor de ataque.

🛠️ Ambiente de Testes

Para a execução segura deste laboratório, foi montado um ambiente isolado utilizando virtualização:

Atacante: Kali Linux (Rolling Edition).

Alvo (Vítima): Metasploitable 2 (máquina propositalmente vulnerável).

Rede: Configuração de Rede Interna / Host-Only no VirtualBox para garantir que o tráfego não saia do ambiente controlado.

🚀 Execução do Projeto

1. Reconhecimento e Enumeração
Antes do ataque, foi realizada uma varredura com Nmap para identificar serviços e portas abertas no alvo.

nmap -sV 192.168.56.101

2. Preparação de Dicionários (Wordlists)
Foram criadas listas customizadas para otimizar o tempo de ataque, simulando o uso de credenciais padrão e senhas fracas.

users.txt: Contas comuns (root, admin, msfadmin, support).

passwords.txt: Senhas previsíveis e a senha alvo para validação do sucesso.

3. Ataque de Força Bruta (Medusa)
A ferramenta Medusa foi utilizada para automatizar as tentativas de login no protocolo FTP.

medusa -h 192.168.56.101 -U users.txt -P passwords.txt -M ftp

Resultados: O Medusa identificou com sucesso as credenciais válidas, permitindo o acesso remoto ao serviço.

🛡️ Estratégias de Defesa e Mitigação

Como resultado desta auditoria, as seguintes recomendações de segurança foram estabelecidas para proteger a infraestrutura:

Políticas de Senhas Fortes: Exigir complexidade (letras, números e símbolos) e rotação frequente.

Bloqueio de Tentativas (Account Lockout): Configurar o sistema para bloquear o IP ou usuário após sucessivas falhas (ex: Fail2Ban).

Autenticação Multifator (MFA): Implementar uma segunda camada de verificação para impedir acessos apenas com senha.

Desativação de Serviços Desnecessários: Manter portas como FTP fechadas se não houver necessidade de uso, priorizando protocolos seguros como SFTP/SSH.

📚 Referências

Kali Linux Official Site

Metasploitable 2 Documentation

Medusa Parallel Network Login Auditor
