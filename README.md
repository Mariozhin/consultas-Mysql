# consultas-Mysql

     /*Consultas relacionadas a Clientes:*/

/*1-Listar todos os clientes cadastrados*/
/*SELECT * FROM Cliente;

Encontrar todos os clientes que são novos (NovoCliente = TRUE).
/*SELECT * FROM Cliente WHERE NovoCliente = TRUE;

/*Recuperar os detalhes de um cliente específico com base no número do cliente.*/
/*SELECT * FROM Cliente WHERE NúmeroCliente = 1;

/*Listar todos os pedidos feitos por um cliente específico.*/
/*SELECT * FROM Pedido WHERE NúmeroCliente = 1;

--------------------------------------------------------------------

     /*Consultas relacionadas a Pedidos:*/

/*Encontrar todos os pedidos feitos em uma data específica.*/
/*SELECT * FROM Pedido WHERE DataPedido = '2023-01-01';

*/Calcular o valor total de todos os pedidos em um determinado mês.*/
/*SELECT MONTH(DataPedido) AS Mês, YEAR(DataPedido) AS Ano, SUM(ValorTotal) AS ValorTotal
FROM Pedido
GROUP BY Mês, Ano;

/*Listar os produtos incluídos em um pedido específico.*/
/*SELECT P.*, PP.NúmeroPedido
FROM Produto P
JOIN PedidoProduto PP ON P.NúmeroProduto = PP.NúmeroProduto
WHERE PP.NúmeroPedido = 1;

/*Recuperar os detalhes do pedido com o maior desconto aplicado.*/
/*SELECT * FROM Pedido ORDER BY Desconto DESC LIMIT 1;

-----------------------------------------------------------------------------------

      /*Consultas relacionadas a Produtos*/
      
/*Listar todos os produtos disponíveis em estoque.*/
/*SELECT * FROM Produto WHERE QuantidadeEstoque > 0;

/*Encontrar produtos com quantidade em estoque abaixo do mínimo ideal.*/
/*SELECT * FROM Produto WHERE QuantidadeEstoque < QtdMinIdealEstoque;

/*Recuperar detalhes de um produto específico.*/
/*SELECT * FROM Produto WHERE NúmeroProduto = 1;

/*Calcular o valor total do estoque.*/
/*SELECT SUM(QuantidadeEstoque) AS ValorTotalEstoque FROM Produto;

-------------------------------------------------------------------------------------

        /*Consultas relacionadas a Fornecedores:*/
        
/*Listar todos os fornecedores cadastrados.*/
/*SELECT * FROM Fornecedor;

/*Recuperar os produtos fornecidos por um fornecedor específico.*/
/*SELECT P.*, PF.CNPJFornecedor
FROM Produto P
JOIN ProdutoFornecedor PF ON P.NúmeroProduto = PF.NúmeroProduto
WHERE PF.CNPJFornecedor = '12345678901234';

/*Encontrar fornecedores inativos.*/
/*SELECT * FROM Fornecedor WHERE CNPJFornecedor NOT IN (SELECT DISTINCT CNPJFornecedor FROM ProdutoFornecedor);

-----------------------------------------------------------------------------------------

       /*Consultas relacionadas a Solicitações de Compra:*/

  /*Listar todas as solicitações de compra em aberto.*/
/*SELECT * FROM SolicitacaoCompra WHERE Situação = 'Em aberto';

/*Recuperar detalhes de uma solicitação de compra específica.*/
/*SELECT * FROM SolicitacaoCompra WHERE NúmeroSolicitacao = 1;

/*Encontrar todas as solicitações de compra feitas para um fornecedor específico.*/
/*SELECT * FROM SolicitacaoCompra WHERE CNPJFornecedor = '12345678901234';

/*Calcular o número total de solicitações de compra encerradas.*/
/*SELECT COUNT(*) AS TotalSolicitacoesEncerradas FROM SolicitacaoCompra WHERE Situação = 'Encerrada';

--------------------------------------------------------------------------------------------------

      /*Envolvendo multiplas tabelas*/

      /* 1- Listar todos os pedidos com detalhes do cliente:*/

/*Mostrar informações sobre cada pedido, incluindo os detalhes do cliente.*/
/*SELECT Pedido.*, Cliente.Nome AS NomeCliente, Cliente.Telefone AS TelefoneCliente
FROM Pedido
JOIN Cliente ON Pedido.NúmeroCliente = Cliente.NúmeroCliente;

/* 2-Encontrar todos os produtos em um pedido com suas quantidades:*/

/*Mostrar os produtos incluídos em um pedido específico, juntamente com as quantidades.*/
/*SELECT Produto.*, PedidoProduto.NúmeroPedido, PedidoProduto.Quantidade
FROM Produto
JOIN PedidoProduto ON Produto.NúmeroProduto = PedidoProduto.NúmeroProduto
WHERE PedidoProduto.NúmeroPedido = 1;

/*3-Listar todos os produtos fornecidos por um fornecedor específico:*/

/*Mostrar os produtos fornecidos por um determinado fornecedor.*/
/*SELECT Produto.*, ProdutoFornecedor.CNPJFornecedor
FROM Produto
JOIN ProdutoFornecedor ON Produto.NúmeroProduto = ProdutoFornecedor.NúmeroProduto
WHERE ProdutoFornecedor.CNPJFornecedor = '12345678901234';

/*4-Recuperar todos os pedidos feitos por clientes novos:*/

/*Listar os pedidos feitos por clientes que são novos.*/
/*SELECT Pedido.*, Cliente.Nome AS NomeCliente
FROM Pedido
JOIN Cliente ON Pedido.NúmeroCliente = Cliente.NúmeroCliente
WHERE Cliente.NovoCliente = TRUE;

       
   
