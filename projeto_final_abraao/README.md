# 🐾 Dr. Animal Pet Shop - CRUD em PHP e SQL

Um sistema simples e funcional de gerenciamento para um pet shop, desenvolvido em **PHP puro** e **MySQL**, com interface responsiva e intuitiva.

## 📋 Características

- ✅ **CRUD Completo** para Clientes, Pets e Serviços
- 🎨 **Interface Responsiva** e moderna com CSS3
- 🔒 **Validação de Dados** no servidor
- 💾 **Banco de Dados MySQL** com relacionamentos
- 🚀 **Fácil de Instalar** e Configurar
- 📱 **Mobile Friendly** - Funciona em qualquer dispositivo

## 📁 Estrutura de Arquivos

```
dr_animal_petshop/
├── config.php              # Configuração e conexão com banco de dados
├── index.php               # Página principal - Listagem de Clientes
├── criar_cliente.php       # Formulário para criar cliente
├── editar_cliente.php      # Formulário para editar cliente
├── pets.php                # Listagem de Pets
├── criar_pet.php           # Formulário para criar pet
├── editar_pet.php          # Formulário para editar pet
├── servicos.php            # Listagem de Serviços
├── criar_servico.php       # Formulário para criar serviço
├── editar_servico.php      # Formulário para editar serviço
├── style.css               # Estilos CSS da aplicação
├── database.sql            # Script SQL para criar banco de dados
└── README.md               # Este arquivo
```

## 🛠️ Requisitos

- **PHP 7.0+** (recomendado PHP 8.0+)
- **MySQL 5.7+** ou **MariaDB 10.2+**
- **Servidor Web** (Apache, Nginx, etc.)
- **Navegador Web** moderno

## 📦 Instalação

### 1. Preparar o Banco de Dados

1. Abra seu cliente MySQL (phpMyAdmin, MySQL Workbench, etc.)
2. Copie e execute o conteúdo do arquivo `database.sql`
3. Isso criará o banco de dados `dr_animal_petshop` com todas as tabelas

**Alternativa via linha de comando:**
```bash
mysql -u root -p < database.sql
```

### 2. Configurar a Conexão

1. Abra o arquivo `config.php`
2. Ajuste as constantes de conexão conforme seu ambiente:

```php
define('DB_HOST', 'localhost');    // Host do MySQL
define('DB_USER', 'root');         // Usuário do MySQL
define('DB_PASS', '');             // Senha do MySQL
define('DB_NAME', 'dr_animal_petshop');  // Nome do banco
```

### 3. Colocar os Arquivos no Servidor

1. Copie todos os arquivos PHP para a pasta `public_html` ou `www` do seu servidor web
2. Certifique-se de que o servidor web tem permissão de leitura e escrita

### 4. Acessar a Aplicação

Abra seu navegador e acesse:
```
http://localhost/dr_animal_petshop/
```

## 🎯 Funcionalidades

### 📋 Clientes
- **Listar** todos os clientes cadastrados
- **Criar** novo cliente com informações pessoais
- **Editar** dados de um cliente existente
- **Deletar** cliente (com confirmação)
- Campos: Nome, Email, Telefone, Endereço, Cidade, Estado, CEP

### 🐶 Pets
- **Listar** todos os pets com informações do cliente
- **Criar** novo pet associado a um cliente
- **Editar** dados de um pet existente
- **Deletar** pet (com confirmação)
- Campos: Nome, Cliente, Espécie, Raça, Data de Nascimento, Peso, Cor, Observações

### ✂️ Serviços
- **Listar** todos os serviços oferecidos
- **Criar** novo serviço
- **Editar** dados de um serviço existente
- **Deletar** serviço (com confirmação)
- Campos: Nome, Descrição, Preço, Duração

## 🔐 Segurança

O sistema implementa as seguintes medidas de segurança:

- **Sanitização de Entrada**: Função `sanitizar()` remove caracteres perigosos
- **Escape de Strings**: Uso de `real_escape_string()` para prevenir SQL Injection
- **Validação de Email**: Validação com `filter_var()`
- **Confirmação de Exclusão**: Confirmação JavaScript antes de deletar
- **Prepared Statements**: Recomendado para futuras melhorias

## 🎨 Customização

### Alterar Cores
Edite o arquivo `style.css` e procure pelas cores principais:
```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

### Adicionar Campos
1. Adicione a coluna na tabela SQL
2. Adicione o campo no formulário HTML
3. Atualize o código PHP de inserção/atualização

### Alterar Tema
Modifique as cores, fontes e estilos no arquivo `style.css`

## 📊 Dados de Exemplo

O banco de dados vem com dados de exemplo:
- **4 Clientes** cadastrados
- **5 Pets** associados aos clientes
- **7 Serviços** disponíveis

Para limpar os dados, execute:
```sql
DELETE FROM pets;
DELETE FROM clientes;
DELETE FROM servicos;
```

## 🐛 Troubleshooting

### Erro: "Erro na conexão com o banco de dados"
- Verifique se o MySQL está rodando
- Confira as credenciais em `config.php`
- Certifique-se de que o banco `dr_animal_petshop` foi criado

### Erro: "Nenhum cliente encontrado"
- Verifique se os dados foram inseridos corretamente
- Acesse o phpMyAdmin e confira as tabelas

### Página em branco
- Verifique o arquivo `config.php`
- Ative o `error_reporting` no PHP para ver erros
- Confira os logs do servidor web

## 📝 Notas Importantes

1. **Backup Regular**: Faça backup do banco de dados regularmente
2. **Senhas Fortes**: Altere a senha padrão do MySQL
3. **HTTPS**: Em produção, use HTTPS para segurança
4. **Validação**: Sempre valide dados no servidor, não apenas no cliente

## 🚀 Melhorias Futuras

- [ ] Autenticação de usuários
- [ ] Dashboard com gráficos
- [ ] Agendamento de serviços
- [ ] Relatórios em PDF
- [ ] API REST
- [ ] Notificações por email
- [ ] Integração com pagamento

## 📄 Licença

Este projeto é de código aberto e pode ser usado livremente.

## 👨‍💻 Suporte

Para dúvidas ou problemas, verifique:
1. Se todos os arquivos estão no mesmo diretório
2. Se o MySQL está rodando
3. Se as permissões de arquivo estão corretas
4. Os logs do servidor web

---

**Desenvolvido com ❤️ para Dr. Animal Pet Shop**

Versão 1.0 - 2024
