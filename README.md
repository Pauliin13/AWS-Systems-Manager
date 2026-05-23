# AWS-Systems-Manager
Visão Geral

Neste laboratório foi utilizado o AWS Systems Manager para gerenciar uma instância Amazon EC2 de forma centralizada e segura, sem necessidade de acesso SSH tradicional.

O laboratório demonstrou como utilizar recursos do Systems Manager para:

Inventário de servidores
Execução remota de comandos
Gerenciamento de parâmetros
Acesso remoto seguro utilizando Session Manager

O objetivo principal foi compreender como empresas administram ambientes Cloud em escala utilizando automação e gerenciamento centralizado.

Objetivos do Laboratório

Ao final deste laboratório foi possível:

Verificar configurações e permissões das instâncias
Executar comandos remotamente utilizando Run Command
Gerenciar parâmetros e configurações de aplicações
Acessar instâncias EC2 sem SSH utilizando Session Manager
Trabalhar com inventário automatizado de servidores
Tecnologias e Serviços Utilizados
Serviço	Descrição
AWS Systems Manager	Gerenciamento centralizado de infraestrutura
Amazon EC2	Instância virtual na AWS
Fleet Manager	Inventário e gerenciamento de servidores
Run Command	Execução remota de comandos
Parameter Store	Armazenamento de parâmetros e configurações
Session Manager	Acesso remoto seguro sem SSH
IAM	Controle de acesso e permissões
AWS CLI	Interface de linha de comando da AWS
Arquitetura do Laboratório

O ambiente consistia em:

Uma instância Amazon EC2 gerenciada
Systems Manager Agent instalado
Gerenciamento centralizado pelo AWS Systems Manager
Aplicação web instalada remotamente
Acesso via Session Manager sem necessidade de SSH

Fluxo do laboratório:

Usuário → AWS Systems Manager → Managed EC2 Instance

Etapa 1 — Configuração de Inventory no Fleet Manager

Nesta etapa foi utilizado o recurso Fleet Manager para coletar informações da instância EC2.

Procedimentos realizados

Acesso ao:

Systems Manager
→ Fleet Manager
→ Set up inventory

Configuração criada:

Campo	Valor
Name	Inventory-Association
Target	Managed Instance
Objetivo do Inventory

O recurso Inventory realiza coleta automática de:

Aplicações instaladas
Pacotes
Configurações
Metadados
Informações do sistema operacional
Resultado

Foi possível visualizar:

Softwares instalados
Dados do sistema
Configurações da instância

Tudo sem necessidade de acesso SSH.

Etapa 2 — Instalação de aplicação utilizando Run Command

Nesta etapa foi utilizado o recurso Run Command para instalar automaticamente uma aplicação web em uma instância EC2.

O que foi instalado

O documento executado realizou automaticamente:

Instalação do Apache Web Server
Instalação do PHP
Instalação do AWS SDK
Deploy da aplicação Widget Manufacturing Dashboard
Procedimentos realizados

Acesso ao:

Systems Manager
→ Run Command
→ Run command

Documento utilizado:

Install Dashboard App

Target configurado:

Managed Instance
Resultado

Após a execução do comando:

O servidor web foi iniciado
A aplicação web foi instalada automaticamente
O dashboard ficou acessível via navegador
Conceito aprendido

O Run Command permite automação de tarefas administrativas em múltiplas instâncias simultaneamente sem necessidade de acesso manual aos servidores.

Etapa 3 — Gerenciamento de parâmetros com Parameter Store

Nesta etapa foi utilizado o Parameter Store para controlar funcionalidades da aplicação.

Configuração criada
Campo	Valor
Name	/dashboard/show-beta-features
Type	String
Value	True
Objetivo

A aplicação consultava automaticamente o parâmetro criado no Systems Manager.

Quando o parâmetro existia:

Recursos beta eram habilitados
Novos gráficos eram exibidos no dashboard
Conceito aprendido

O Parameter Store permite gerenciamento centralizado de:

Configurações
Variáveis
Segredos
Tokens
Strings de conexão

Sem necessidade de alterar diretamente o código da aplicação.

Etapa 4 — Acesso remoto com Session Manager

Nesta etapa foi utilizado o Session Manager para acessar a instância EC2 sem SSH.

Procedimentos realizados

Acesso ao:

Systems Manager
→ Session Manager
→ Start session

Instância utilizada:

Managed Instance
Comandos executados
Listagem dos arquivos da aplicação
ls /var/www/html
Consulta de região AWS
AZ=`curl -s http://169.254.169.254/latest/meta-data/placement/availability-zone`
export AWS_DEFAULT_REGION=${AZ::-1}
Consulta das instâncias EC2
aws ec2 describe-instances
Resultado

Foi possível:

Acessar o shell Linux diretamente pelo navegador
Executar comandos administrativos
Consultar informações EC2 via AWS CLI
Trabalhar sem abrir portas SSH
Conceitos Técnicos Aprendidos
Conceito	Descrição
Systems Manager	Gerenciamento centralizado AWS
Fleet Manager	Inventário e administração de instâncias
Run Command	Execução remota de comandos
Parameter Store	Armazenamento de parâmetros
Session Manager	Acesso remoto sem SSH
Managed Instance	Instância registrada no Systems Manager
SSM Agent	Agente de comunicação do Systems Manager
IAM	Controle de acesso e permissões
Benefícios do AWS Systems Manager

O laboratório demonstrou diversas vantagens do Systems Manager:

Maior segurança
Eliminação da necessidade de SSH
Gerenciamento centralizado
Automação de tarefas
Auditoria via CloudTrail
Escalabilidade operacional
Administração em larga escala
Aprendizados do Laboratório

Este laboratório demonstrou como administrar infraestrutura AWS de maneira moderna utilizando automação e gerenciamento centralizado.

Os principais aprendizados envolveram:

Automação de administração de servidores
Execução remota de tarefas
Gerenciamento de configurações
Segurança operacional
Administração sem SSH
Utilização prática do Systems Manager
Conclusão

Ao concluir este laboratório, foi possível compreender como o AWS Systems Manager simplifica o gerenciamento de infraestrutura Cloud por meio de automação, segurança e administração centralizada.

O uso de recursos como Fleet Manager, Run Command, Parameter Store e Session Manager demonstra práticas amplamente utilizadas em ambientes corporativos modernos de Cloud Computing e DevOps.

Autor

Paulo Henrique Pereira Dos Santos

Referências
Documentação oficial AWS Systems Manager
AWS Skill Builder
Documentação Amazon EC2
Documentação IAM
AWS CLI Documentation
