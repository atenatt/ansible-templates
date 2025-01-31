﻿# **Ansible Templates**

Este repositório contém templates úteis para configurar e gerenciar servidores com **Ansible**. A estrutura inclui exemplos para:

- **Configuração de nó único (single-node)**
- **Configuração multi-nó (multi-node)**
- **Exemplo de uso de roles**
- **Playbooks avançados para MariaDB e Webserver**
- **Exemplos simples para administração de sistemas** (Criação de usuário, diretórios, cópia de arquivos, etc.)

Esses templates podem ser usados como base para a automação de tarefas de administração de sistemas e infraestrutura.

## Estrutura do Repositório

O repositório está organizado da seguinte forma:

```
ansible-templates/
├── README.md               # Este arquivo
├── templates/
│   ├── single-node/        # Exemplo de configuração para um único nó
│   ├── multi-node/         # Exemplo de configuração para múltiplos nós
|   ├── cron-modules/       # Exemplo de configuração para agendamento de tarefas com Cron.
│   ├── roles-example/      # Exemplo de roles do Ansible
│   ├── simple-examples/    # Exemplos simples para administração de sistemas
├── advanced-examples/      # Exemplos avançados de configuração e playbooks
└── .gitignore
```

## Como Usar

### 1. **Clone o Repositório**

Primeiro, clone o repositório em seu ambiente local:

```bash
git clone https://github.com/seu-usuario/ansible-templates.git
cd ansible-templates
```

### 2. **Configuração do Inventário**

Os exemplos de inventário estão localizados nas pastas:

- **single-node/inventory.ini** - Usado para um único nó.
- **multi-node/inventory.ini** - Usado para múltiplos nós.
- **advanced-examples/mariadb/inventory.ini** - Exemplo para servidores MariaDB.
- **simple-examples/inventory.ini** - Inventário para exemplos simples.

Edite o arquivo **`inventory.ini`** conforme a necessidade, substituindo os IPs dos servidores.

### 3. **Configuração do Ansible**

O arquivo **`ansible.cfg`** está configurado para usar o arquivo de inventário correto e outras opções úteis como `host_key_checking = False` (para evitar verificações de chave SSH).

Você pode ajustar esse arquivo de configuração conforme necessário para se adequar ao seu ambiente.

### 4. **Playbooks**

#### **Single Node (Nó Único)**

Para rodar o playbook de um único nó:

```bash
ansible-playbook -i templates/single-node/inventory.ini templates/single-node/playbook.yml
```

#### **Multi Node (Múltiplos Nós)**

Para rodar o playbook de múltiplos nós:

```bash
ansible-playbook -i templates/multi-node/inventory.ini templates/multi-node/playbook.yml
```

#### **Exemplo de Role: Webserver**

Este exemplo instala o Apache e configura um servidor virtual com base em um template.

1. Edite o arquivo **`advanced-examples/webserver-role/vars/main.yml`** para definir o nome do servidor e o diretório raiz.

2. Execute o playbook de role para o Webserver:

```bash
ansible-playbook -i templates/roles-example/inventory.ini advanced-examples/webserver-role/tasks/main.yml
```

#### **Exemplo Avançado: MariaDB**

Este exemplo configura um servidor MariaDB, incluindo a instalação e configuração do serviço com um arquivo de configuração.

1. Edite o arquivo **`advanced-examples/mariadb/templates/mariadb.cnf.j2`** conforme a necessidade.

2. Execute o playbook para configurar o MariaDB:

```bash
ansible-playbook -i advanced-examples/mariadb/inventory.ini advanced-examples/mariadb/playbook.yml
```

#### **Exemplos Simples para Administração de Sistemas**

Esta pasta contém playbooks simples para tarefas como:

- Criação de usuários
- Criação de diretórios
- Cópia de arquivos

Para rodar esses playbooks, use o seguinte comando:

```bash
ansible-playbook -i templates/simple-examples/inventory.ini templates/simple-examples/create-user.yml
ansible-playbook -i templates/simple-examples/inventory.ini templates/simple-examples/create-directory.yml
ansible-playbook -i templates/simple-examples/inventory.ini templates/simple-examples/copy-file.yml
```

### 5. **Variáveis e Templates**

Os arquivos de template são usados para gerar configurações dinâmicas. Por exemplo:

- **`advanced-examples/webserver-role/templates/vhost.conf.j2`**: Um template para configurar o Apache com variáveis, como `server_name` e `document_root`.
- **`advanced-examples/mariadb/templates/mariadb.cnf.j2`**: Template de configuração do MariaDB, incluindo variáveis dinâmicas como o endereço IP do servidor.
- **`simple-examples/templates/config.j2`**: Template simples para configurar arquivos de texto com variáveis dinâmicas.

### 6. **Personalização**

Você pode modificar qualquer um dos templates ou playbooks para se adaptar às suas necessidades. Algumas áreas comuns para personalização incluem:

- Endereços IP e credenciais de acesso no arquivo de inventário.
- Variáveis no arquivo **`vars/main.yml`** para roles e templates.
- Parâmetros específicos de serviços no playbook.

### 7. **Requisitos**

Para usar os templates, você precisará ter o **Ansible** instalado. Para instalá-lo, siga os passos:

- **No Ubuntu/Debian**:

  ```bash
  sudo apt update
  sudo apt install ansible
  ```

- **No CentOS/RHEL**:

  ```bash
  sudo yum install ansible
  ```

- **No macOS** (usando Homebrew):

  ```bash
  brew install ansible
  ```

## Contribuições

Se você deseja contribuir com novos templates ou melhorias, sinta-se à vontade para abrir um pull request. Algumas áreas que podem ser aprimoradas:

- **Mais exemplos de roles**: Como configurar serviços adicionais, como Nginx, Docker, etc.
- **Documentação adicional**: Exemplos específicos de uso e explicações detalhadas.

---

### **Explicação do README.md**

1. **Estrutura do Repositório**: Uma visão geral do que cada diretório contém.
2. **Como Usar**: Passos claros para começar, incluindo como clonar o repositório, configurar o inventário e rodar os playbooks.
3. **Exemplos**: Exemplos de playbooks para diferentes cenários e como usar os templates.
4. **Personalização**: Dicas sobre como adaptar os arquivos para seu ambiente.
5. **Requisitos**: Instruções sobre como instalar o Ansible.
6. **Contribuições**: Como contribuir para o repositório com novos templates ou melhorias.
7. **Licença**: Informação sobre a licença do projeto.
