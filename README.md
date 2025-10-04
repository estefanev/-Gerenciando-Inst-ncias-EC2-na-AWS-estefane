🖥️ Gerenciamento de Instâncias EC2 na AWS

📌 Sobre o Projeto

Este repositório faz parte do desafio proposto pela DIO (Digital Innovation One) para consolidar os conhecimentos adquiridos em AWS EC2.
O objetivo é demonstrar a criação, configuração e gerenciamento de uma instância EC2, documentando cada etapa de forma clara e organizada.

🎯 Objetivos de Aprendizagem

Ao final deste laboratório, foi possível:

Criar e gerenciar instâncias EC2 na AWS;

Configurar Security Groups com boas práticas;

Conectar-se à instância via SSH/EC2 Instance Connect;

Aplicar scripts de inicialização (User Data);

Documentar o processo no GitHub como portfólio técnico.

⚙️ Ambiente Utilizado

Plataforma Cloud: Amazon Web Services (AWS)

Serviço: EC2 (Elastic Compute Cloud)

SO da Instância: Amazon Linux 2 (AMI padrão)

Tipo de Instância: t2.micro (free tier)

Armazenamento: 8 GiB (EBS SSD gp2)

Rede: VPC default + Subnet pública

Acesso:

Par de chaves (Key Pair) para SSH

Security Group configurado (porta 22 liberada para meu IP)

📝 Passo a Passo do Laboratório

1️⃣ Criação da Instância EC2

AMI escolhida: Amazon Linux 2

Tipo de instância: t2.micro

Key Pair: meu-par-ec2.pem criado para acesso SSH

Storage: 8 GiB SSD gp2

📸 Print da criação da instância:


2️⃣ Configuração de Security Group

Porta 22 (SSH) liberada apenas para meu IP.

Porta 80 (HTTP) liberada para acesso público (caso de servidor web).

📸 Print do Security Group:


3️⃣ Conexão à Instância

Conexão realizada via terminal:

ssh -i "meu-par-ec2.pem" ec2-user@<IP_DA_INSTANCIA>


📸 Print da conexão via SSH:


4️⃣ Script de Inicialização (User Data)

Foi utilizado um script para instalação automática do Apache:

#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
echo "<h1>Servidor EC2 configurado com sucesso!</h1>" > /var/www/html/index.html


📸 Print do servidor web rodando:


5️⃣ Encerramento/Parada da Instância

Após os testes, a instância foi parada para evitar custos.
📸 Print da instância parada:


💡 Insights e Aprendizados

Sempre restringir o Security Group para evitar exposição da instância.

Scripts de User Data economizam tempo e garantem padronização.

Uso de tags é essencial para organização em ambientes corporativos.

Boas práticas de shutdown evitam custos desnecessários.

📂 Estrutura do Repositório
📦 aws-ec2-gerenciamento
 ┣ 📂 images
 ┃ ┣ criacao-ec2.png
 ┃ ┣ security-group.png
 ┃ ┣ conexao-ssh.png
 ┃ ┗ apache-running.png
 ┣ 📂 scripts
 ┃ ┗ user-data.sh
 ┗ 📜 README.md

📚 Referências

AWS EC2 - Documentação Oficial

AWS Free Tier

Guia de boas práticas em segurança na AWS
