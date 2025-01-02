## **simple-examples**

Esta pasta contém exemplos simples de playbooks do **Ansible** para realizar tarefas comuns, como:

- Criação de usuários no sistema
- Criação de diretórios
- Cópia de arquivos para destinos específicos

Esses exemplos são ideais para quem está começando com o Ansible e deseja entender as operações básicas.

## Estrutura da Pasta

```
simple-examples/
├── create-user.yml        # Playbook para criar usuário
├── create-directory.yml   # Playbook para criar diretório
├── copy-file.yml          # Playbook para copiar arquivos
└── files/
    └── myconfig.conf      # Arquivo de configuração de exemplo
```

## Como Usar

### 1. **Criar Usuário**

Este playbook cria um usuário chamado `admin` e o adiciona ao grupo `sudo`, além de definir um shell padrão. 

**Executar**:

```bash
ansible-playbook -i inventory.ini templates/simple-examples/create-user.yml
```

### 2. **Criar Diretório**

Este playbook cria o diretório `/var/log/custom` com permissões de leitura, escrita e execução para o dono (root) e leitura e execução para os outros.

**Executar**:

```bash
ansible-playbook -i inventory.ini templates/simple-examples/create-directory.yml
```

### 3. **Copiar Arquivo**

Este playbook copia o arquivo de configuração **`myconfig.conf`** para o diretório `/etc`. O arquivo de configuração está na pasta **`files/`**.

**Executar**:

```bash
ansible-playbook -i inventory.ini templates/simple-examples/copy-file.yml
```

> **Nota**: Para que o playbook de cópia de arquivos funcione corretamente, você deve ter o arquivo **`myconfig.conf`** dentro da pasta **`files/`**.

## Pré-Requisitos

Antes de rodar os playbooks, verifique se o **Ansible** está instalado no seu sistema. Você pode instalar o Ansible com os seguintes comandos:

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

## Personalização

Você pode personalizar os playbooks conforme sua necessidade. Por exemplo:

- No playbook **`create-user.yml`**, altere o nome do usuário, o grupo ou a senha.
- No playbook **`create-directory.yml`**, modifique o caminho e as permissões do diretório.
- No playbook **`copy-file.yml`**, adicione outros arquivos ou altere o destino.
