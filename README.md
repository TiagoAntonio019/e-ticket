# e-Ticket
![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-005C84?style=for-the-badge&logo=mysql&logoColor=white)

e-Ticker é um projeto Mysql feito para ajudar na organização de estacionamento de Shopping.

<img src="https://i.ibb.co/d5BtBDD/e-Ticket-drawio.png" alt="e-Ticket-drawio" border="0">

## Features
- Registrar entrada do cliente
- Registrar saída do cliente.
- Calcular o valor a cobrar pelo serviço de estacionamento.
- Calculo de tempo médio de utilização de uma vaga.
- Receita em um dado período.

## Como utilizar

### Instalar MySQL (Container DOcker)
__Caso você já tenha o MySQL instalado vá para o próximo tópico (preprando o Mysql).__

Baixe a versão mais recente do Mysql

```
docker pull mysql
```
Crie seu container
```
sudo docker run -p 3306:3306 --name mysql_container_name -e MYSQL_ROOT_PASSWORD=12345 -d mysql
```

### Preparando o MySQL
Nesse primeiro momento do projeto será necessário criar o banco de dados manualmente:
Acessando o MySQL Server com client
```
mysql -h 127.0.0.1 -P 3307 -u root -p
```
- -h: endereço IP do MySQL Server.
- -P: porta que o serviço está ouvindo, no meu caso está na 3307 (padrão 3306).
- -u: usuário.
- -p: senha que será solicitada logo após rodar o comando citado acima.

Caso você não tenha o MySQL client instalado basta rodar o seguinte comando:
```
sudo apt install mysql-client
```
Agora vamos criar nosso db:
```sql
create database eticket;
```
Agora podemos subir o projeto, digite `quit`, localize o arquivo `eticket.sql` e digite o seguinte comando:
```
mysql -h 127.0.0.1 -P 3307 -u root -p eticket < eticket.sql
```
Agora podemos testar o projeto, entre novamente no MySQL Server e teste a procedure `create_ticket()`:
```
mysql -h 127.0.0.1 -P 3307 -u root -p
```
```sql
call create_ticket();
```
A mensagem "Ticket criado" deverá ser retornada.