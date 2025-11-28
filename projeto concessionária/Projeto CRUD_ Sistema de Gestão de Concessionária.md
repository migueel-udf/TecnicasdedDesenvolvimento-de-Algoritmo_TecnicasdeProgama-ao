# Projeto CRUD: Sistema de Gestão de Concessionária

Este projeto consiste em uma aplicação web desenvolvida em **PHP** com **MySQL** para realizar operações de **CRUD (Create, Read, Update, Delete)** em um sistema de gestão de concessionária. O sistema permite o gerenciamento de Clientes, Funcionários, Marcas, Modelos e Vendas.

## Breve Descrição do Trabalho

O objetivo principal deste trabalho é demonstrar a implementação de um sistema de gerenciamento de dados utilizando a arquitetura CRUD. A aplicação é focada na gestão de entidades chave em um contexto de concessionária, proporcionando uma interface simples para a manipulação dos registros no banco de dados.

## Projeto Desenvolvido com Aplicação CRUD

O projeto abrange as seguintes entidades, cada uma com suas respectivas operações CRUD:

| Entidade | Operações CRUD | Arquivos Principais |
| :--- | :--- | :--- |
| **Cliente** | Cadastro, Listagem, Edição, Exclusão | `cadastrar-cliente.php`, `listar-cliente.php`, `editar-cliente.php`, `salvar-cliente.php` |
| **Funcionário** | Cadastro, Listagem, Edição, Exclusão | `cadastrar-funcionario.php`, `listar-funcionario.php`, `editar-funcionario.php`, `salvar-funcionario.php` |
| **Marca** | Cadastro, Listagem, Edição, Exclusão | `cadastrar-marca.php`, `listar-marca.php`, `editar-marca.php`, `salvar-marca.php` |
| **Modelo** | Cadastro, Listagem, Edição, Exclusão | `cadastrar-modelo.php`, `listar-modelo.php`, `editar-modelo.php`, `salvar-modelo.php` |
| **Venda** | Cadastro, Listagem, Edição, Exclusão | `cadastrar-venda.php`, `listar-venda.php`, `editar-venda.php`, `salvar-venda.php` |

O banco de dados utilizado é o `concessionariaberg`, cuja estrutura está definida no arquivo `bancodedados.sql`.

## Especificação em Linguagem Algorítmica (PHP/SQL)

A aplicação foi desenvolvida utilizando a linguagem de programação **PHP** para o *backend* e **SQL** (MySQL) para a persistência de dados. A lógica de manipulação de dados é centralizada em arquivos como `salvar-cliente.php`, que utiliza a variável global `$_REQUEST['acao']` para determinar a operação CRUD a ser executada.

### Exemplo de Implementação CRUD (Baseado em `salvar-cliente.php`)

```php
<?php 
    // O arquivo config.php deve conter a conexão com o banco de dados ($conn)
    include("config.php"); 

    switch ($_REQUEST['acao']) {
        case 'cadastrar':
            $nome = $_POST['nome_cliente'];
            $email = $_POST['email_cliente'];
            // ... outras variáveis

            $sql = "INSERT INTO cliente (nome_cliente, cpf_cliente, email_cliente, telefone_cliente, endereco_cliente, dt_nasc_cliente)
                    VALUES ('{$nome}', '{$cpf}', '{$email}', '{$telefone}', '{$endereco}', '{$dt_nasc}')";

            $res = $conn->query($sql);

            if($res == true){
                print "<script>alert('Cadastrou com sucesso!');</script>";
                print "<script>location.href='?page=listar-cliente';</script>";
            }else{
                print "<script>alert('Não Cadastrou!');</script>";
                print "<script>location.href='?page=listar-cliente';</script>";
            }
            break;
            
        case 'editar':
            // ... obtenção de variáveis
            $sql = "UPDATE cliente SET nome_cliente='{$nome}', email_cliente='{$email}', telefone_cliente='{$telefone}', cpf_cliente='{$cpf}', endereco_cliente='{$endereco}', dt_nasc_cliente='{$dt_nasc}' WHERE id_cliente=".$_REQUEST['id_cliente'];
            // ... execução e feedback
            break;

        case 'excluir':
            $sql = "DELETE FROM cliente WHERE id_cliente=".$_REQUEST['id_cliente'];
            // ... execução e feedback
            break;
    }
?>
```

## Pseudocódigo

O pseudocódigo a seguir representa a lógica genérica de execução de uma operação CRUD na aplicação:

```
INÍCIO
  FUNÇÃO ConectarBancoDeDados(HOST, USUARIO, SENHA, BANCO, PORTA)
    TENTAR
      Conexão = NovaConexão(HOST, USUARIO, SENHA, BANCO, PORTA)
      RETORNAR Conexão
    EXCEÇÃO
      IMPRIMIR "Erro ao conectar ao banco de dados."
      SAIR
  FIM FUNÇÃO

  FUNÇÃO ExecutarCRUD(Acao, Tabela, Dados, Condicao)
    SE Acao = "CADASTRAR" ENTÃO
      Campos = ObterCampos(Dados)
      Valores = ObterValores(Dados)
      SQL = "INSERT INTO " + Tabela + " (" + Campos + ") VALUES (" + Valores + ")"
    SENÃO SE Acao = "EDITAR" ENTÃO
      SetClause = CriarSetClause(Dados)
      SQL = "UPDATE " + Tabela + " SET " + SetClause + " WHERE " + Condicao
    SENÃO SE Acao = "EXCLUIR" ENTÃO
      SQL = "DELETE FROM " + Tabela + " WHERE " + Condicao
    SENÃO SE Acao = "LISTAR" ENTÃO
      SQL = "SELECT * FROM " + Tabela
    SENÃO
      IMPRIMIR "Ação CRUD inválida."
      RETORNAR FALSO
    FIM SE

    TENTAR
      Resultado = Conexão.ExecutarQuery(SQL)
      SE Resultado = SUCESSO ENTÃO
        RETORNAR VERDADEIRO
      SENÃO
        RETORNAR FALSO
      FIM SE
    EXCEÇÃO
      IMPRIMIR "Erro ao executar a query: " + SQL
      RETORNAR FALSO
    FIM TENTAR
  FIM FUNÇÃO

  // Exemplo de Uso (Baseado em salvar-cliente.php)
  SE REQUISICAO.acao = "cadastrar" ENTÃO
    DadosCliente = {
      "nome_cliente": REQUISICAO.POST.nome_cliente,
      "cpf_cliente": REQUISICAO.POST.cpf_cliente,
      // ... outros campos
    }
    Resultado = ExecutarCRUD("CADASTRAR", "cliente", DadosCliente, NULO)
    SE Resultado = VERDADEIRO ENTÃO
      IMPRIMIR "Cadastrou com sucesso!"
      REDIRECIONAR "listar-cliente"
    SENÃO
      IMPRIMIR "Não Cadastrou!"
      REDIRECIONAR "listar-cliente"
    FIM SE
  FIM SE
FIM
```

## Fluxograma

O fluxograma a seguir ilustra o fluxo de controle para a execução de qualquer operação CRUD na aplicação:

![Fluxograma do Processo CRUD](https://private-us-east-1.manuscdn.com/sessionFile/78M9LmRsxUCKNfqlFpY3Ya/sandbox/Fkb9E6gQnyz0Oh9RTjlZam-images_1764285549787_na1fn_L2hvbWUvdWJ1bnR1L3Byb2pldG9zX2NydWQvZmx1eG9ncmFtYQ.png?Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9wcml2YXRlLXVzLWVhc3QtMS5tYW51c2Nkbi5jb20vc2Vzc2lvbkZpbGUvNzhNOUxtUnN4VUNLTmZxbEZwWTNZYS9zYW5kYm94L0ZrYjlFNmdRbnl6ME9oOVJUamxaYW0taW1hZ2VzXzE3NjQyODU1NDk3ODdfbmExZm5fTDJodmJXVXZkV0oxYm5SMUwzQnliMnBsZEc5elgyTnlkV1F2Wm14MWVHOW5jbUZ0WVEucG5nIiwiQ29uZGl0aW9uIjp7IkRhdGVMZXNzVGhhbiI6eyJBV1M6RXBvY2hUaW1lIjoxNzk4NzYxNjAwfX19XX0_&Key-Pair-Id=K2HSFNDJXOU9YS&Signature=hqYG2o9A2m0oUOkEJiD-Jfmmu9sI8tUnwzJCwPSx2LonT7rQRDD65EkZ6BXdI2rFo6legvFgjFeW8cUeH69Kmjj2MbZyl4XHmiW0OhqYHnj2lwYQ1xLMWa29zHTVheLu3j~5IUTLAFiWAZMvpuOWufpf-dKlWz29df7b7DPDmxI9LIc0cqOEHs2lUPvh5OOEqeFEUkHEjkFjhJ1yb4zwpu7wNZOuF3hDvmBYMDka-X1k2g66UJnRXxwINfxjqA4GKXCNFQ7hb3YWnnyjDKPGA22gUW~2d4m-tjm6qRb9yGcR67ZNTBHLcHXN49r9CGoKyvWpqnEaYHOhnYgnh0ictg__)

## Instruções de Instalação

Para instalar e executar o projeto, você precisará de um ambiente de servidor web que suporte PHP e MySQL (como XAMPP, WAMP ou MAMP).

1.  **Baixe e Configure o Servidor Web:**
    *   Instale o XAMPP (ou equivalente).
    *   Inicie os serviços **Apache** e **MySQL**.

2.  **Configuração do Banco de Dados:**
    *   Acesse o painel de administração do MySQL (geralmente `http://localhost/phpmyadmin`).
    *   Crie um novo banco de dados com o nome `concessionariaberg`.
    *   Importe o arquivo `bancodedados.sql` para este novo banco de dados.

3.  **Configuração do Projeto:**
    *   Mova a pasta `projetos` (contida no zip) para o diretório raiz do seu servidor web (ex: `htdocs` no XAMPP).
    *   Verifique e, se necessário, ajuste as configurações de conexão no arquivo `config.php`:

        ```php
        <?php
            define('HOST', 'localhost');
            define('USER', 'root');
            define('PASS', ''); // Senha padrão do XAMPP é vazia
            define('BASE', 'concessionariaberg');
            define('PORT', 3307); // Porta padrão do MySQL no XAMPP
            
            $conn = new MySQLi(HOST,USER,PASS,BASE,PORT);
        ?>
        ```

## Passos para Execução

1.  Certifique-se de que os serviços **Apache** e **MySQL** estão em execução.
2.  Abra seu navegador web.
3.  Acesse a URL do projeto, que será algo como:
    `http://localhost/projetos/index.php`
4.  A partir da página inicial (`index.php`), você poderá navegar para as telas de cadastro e listagem de cada entidade (Clientes, Funcionários, Marcas, Modelos e Vendas) para realizar as operações CRUD.
