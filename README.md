```markdown
# Projeto de E-commerce - Modelo de Banco de Dados e Consultas SQL

## Descrição do Projeto

Este projeto consiste na criação de um modelo de banco de dados para um cenário de e-commerce, juntamente com a implementação de consultas SQL que atendam a requisitos específicos. O objetivo é desenvolver um esquema lógico que permita armazenar informações sobre clientes, produtos, pedidos, pagamentos, fornecedores e vendedores, além de criar consultas para extrair informações relevantes do banco de dados.

## Modelagem do Banco de Dados

O modelo de banco de dados foi desenvolvido com base nos requisitos do cenário de e-commerce e inclui as seguintes tabelas:

1. `clients`: Armazena informações sobre os clientes do e-commerce, como nome, CPF, endereço, entre outros.

2. `product`: Contém detalhes dos produtos disponíveis para venda, como nome, categoria, tamanho, classificação para crianças, etc.

3. `orders`: Registra informações sobre os pedidos realizados pelos clientes, como status, descrição, valor de envio e método de pagamento.

4. `payment`: Armazena as diferentes formas de pagamento disponíveis para cada cliente.

5. `productStorage`: Gerencia o estoque dos produtos, incluindo a localização do armazenamento e a quantidade disponível.

6. `supplier`: Registra os fornecedores de produtos para o e-commerce, com detalhes como razão social, CNPJ e informações de contato.

7. `seller`: Contém informações sobre os vendedores que atuam no e-commerce, incluindo razão social, CNPJ, CPF e detalhes de contato.

8. `productSeller`: Relaciona os produtos vendidos por cada vendedor, juntamente com a quantidade disponível para venda.

9. `productOrder`: Relaciona os produtos presentes em cada pedido, incluindo a quantidade solicitada e o status do produto no pedido.

10. `storageLocation`: Gerencia a localização dos produtos no estoque.

11. `productSupplier`: Estabelece o relacionamento entre os produtos e os fornecedores que os fornecem, com detalhes sobre a quantidade fornecida.

## Executando as Consultas SQL

Para executar as consultas SQL e testar o funcionamento do banco de dados, siga as etapas abaixo:

1. Clone este repositório para o seu computador:
   ```
   git clone https://github.com/seu-usuario/nome-do-repositorio.git
   ```

2. Importe o arquivo `ecommerce.sql` para criar o banco de dados e as tabelas:
   ```
   mysql -u seu-usuario -p < ecommerce.sql
   ```

3. Agora, você pode executar as consultas SQL que atendem aos requisitos específicos do desafio. Abra o terminal do MySQL e digite as queries desejadas.

Exemplos de algumas queries disponíveis:

- Exemplo 1: Recupera todos os clientes do e-commerce:
  ```
  SELECT * FROM clients;
  ```

- Exemplo 2: Recupera os produtos disponíveis em estoque na localização 'Loja A':
  ```
  SELECT Fname, size, quantity FROM product
  INNER JOIN storageLocation ON product.idProduct = storageLocation.idLproduct
  INNER JOIN productStorage ON storageLocation.idLstorage = productStorage.idProductStorage
  WHERE storageLocation = 'Loja A';
  ```

- Exemplo 3: Recupera o valor total de pedidos confirmados:
  ```
  SELECT SUM(sendValue) AS valor_total_pedidos FROM orders WHERE orderStatus = 'Confirmado';
  ```
