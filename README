# Infraestrutura com Terraform e Ansible

Este repositório contém a infraestrutura como código (IaC) utilizando Terraform para provisionamento na AWS e Ansible para configuração de um ambiente Django. Todos os recursos utilizados neste projeto estão dentro do **Free Tier da AWS**, permitindo que sejam testados sem custos adicionais.

## 📌 Visão Geral
- O Terraform cria uma VPC, subnets, um grupo de segurança, uma instância EC2 e um banco de dados PostgreSQL.
- O Ansible configura a instância EC2 instalando dependências e inicializando um projeto Django.
- **Todos os recursos utilizados estão dentro do Free Tier da AWS**.

## 🛠️ Pré-requisitos
Antes de utilizar este projeto, certifique-se de ter instalado:

- [Terraform](https://developer.hashicorp.com/terraform/downloads)
- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
- [AWS CLI](https://aws.amazon.com/cli/) configurado com credenciais válidas

## 🚀 Implantação com Terraform

### 1️⃣ Configuração Inicial
Altere a chave SSH na linha 65 do arquivo Terraform para a sua chave:
```hcl
key_name = "SUA_CHAVE_SSH"
```

### 2️⃣ Aplicação do Terraform

Execute os seguintes comandos para criar a infraestrutura na AWS:
```sh
terraform init
terraform apply -auto-approve
```
Ao final, será criada uma instância EC2 e um banco de dados PostgreSQL na AWS.

## ⚙️ Configuração com Ansible

Após a infraestrutura estar provisionada, use o Ansible para configurar o ambiente Django na instância EC2.

### 1️⃣ Atualize o arquivo de inventário
Crie um arquivo `inventory.ini` e adicione o IP da instância EC2 criada pelo Terraform:
```ini
[terraform-ansible]
SEU_IP_EC2 ansible_user=ubuntu ansible_ssh_private_key_file=SUA_CHAVE_SSH.pem
```

### 2️⃣ Execute a Playbook
```sh
ansible-playbook -i inventory.ini playbook.yml
```
Este comando instalará o Python, Django e iniciará um projeto Django no servidor.

## 📌 Recursos Criados
- **VPC:** 10.0.0.0/16
- **Subnets:**
  - 10.0.1.0/24 (us-east-1a)
  - 10.0.2.0/24 (us-east-1b)
- **Grupo de Segurança:** Acesso ao PostgreSQL (porta 5432) e comunicação geral.
- **Instância EC2:** Ubuntu com chave SSH configurável.
- **Banco de Dados PostgreSQL:** `db.t4g.micro` na AWS.

## 📝 Observações
- Por segurança, altere a configuração `cidr_blocks = ["0.0.0.0/0"]` no grupo de segurança para restringir o acesso ao banco de dados.
- Altere `ALLOWED_HOSTS = ["*"]` no Django para restringir os domínios permitidos.

## 🧹 Destruição da Infraestrutura
Para remover todos os recursos criados, execute:
```sh
terraform destroy -auto-approve
```

## 📜 Licença
Este projeto está licenciado sob a licença MIT.

---
Desenvolvido para automação de infraestrutura e configuração de aplicações Django na AWS. 🚀

