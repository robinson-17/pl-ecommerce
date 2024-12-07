# pl-ecommerce

### Descrição Completa do Projeto Lógico - Esquema de Banco de Dados para E-Commerce

O esquema lógico apresentado tem como objetivo estruturar um sistema de banco de dados para uma plataforma de comércio eletrônico. Ele foi projetado para atender às principais necessidades de um e-commerce, incluindo gestão de produtos, clientes (Pessoa Física e Jurídica), fornecedores, estoques, pagamentos, e entregas. Abaixo está uma descrição detalhada de cada componente do modelo:

---

### **1. Cliente**
O sistema suporta dois tipos de clientes: Pessoa Física (PF) e Pessoa Jurídica (PJ). A abordagem utiliza uma tabela genérica `Cliente` que armazena informações comuns a todos os tipos de cliente e se relaciona com tabelas específicas para Pessoa Física (`ClientePF`) e Pessoa Jurídica (`ClientePJ`).

- **Tabela `Cliente`:**
  - Contém informações gerais como nome, email, telefone, endereço, e tipo de cliente.
  - Relaciona-se com as tabelas `ClientePF` e `ClientePJ` através do campo `idCliente`.

- **Tabela `ClientePF`:**
  - Contém informações específicas para clientes pessoa física, como CPF e data de nascimento.

- **Tabela `ClientePJ`:**
  - Contém informações específicas para clientes pessoa jurídica, como CNPJ e nome fantasia.

---

### **2. Produto e Estoque**
O gerenciamento de produtos e estoques foi projetado para permitir rastreamento detalhado da disponibilidade de produtos e localização.

- **Tabela `Produto`:**
  - Contém informações gerais sobre os produtos, como nome e descrição.

- **Tabela `Estoque`:**
  - Representa os locais de armazenamento, com informações como ID e localização.

- **Tabela `Produto_has_Estoque`:**
  - Implementa um relacionamento de muitos-para-muitos entre `Produto` e `Estoque`, permitindo rastrear a quantidade de cada produto em diferentes locais de armazenamento.

---

### **3. Fornecedores e Disponibilização de Produtos**
Os fornecedores e a disponibilização de produtos seguem uma estrutura que facilita o rastreamento das origens dos produtos vendidos.

- **Tabela `Fornecedor`:**
  - Armazena informações básicas sobre os fornecedores, como razão social e CNPJ.

- **Tabela `Disponibilizado_produto`:**
  - Relaciona fornecedores com produtos disponibilizados, permitindo gerenciar quais produtos cada fornecedor oferece.

---

### **4. Produtos de Terceiros**
O sistema suporta produtos vendidos por terceiros (marketplace), criando uma estrutura separada para rastrear essas transações.

- **Tabela `Terceiro_Vendedor`:**
  - Contém informações sobre vendedores terceiros.

- **Tabela `Produtos/Vendedor (terceiros)`:**
  - Relaciona produtos com vendedores terceiros, especificando as quantidades.

---

### **5. Pedidos**
Os pedidos são o núcleo do sistema de e-commerce, com relacionamentos abrangendo produtos, clientes, pagamentos e entregas.

- **Tabela `Pedido`:**
  - Contém informações gerais sobre os pedidos, incluindo status, descrição, e cliente associado.

- **Tabela `Relacao_Produto/Pedido`:**
  - Implementa um relacionamento de muitos-para-muitos entre produtos e pedidos, armazenando as quantidades de cada produto em um pedido.

---

### **6. Pagamento**
A estrutura de pagamento foi projetada para permitir múltiplas formas de pagamento por pedido.

- **Tabela `Pagamento`:**
  - Armazena informações como forma de pagamento (cartão de crédito, boleto, PIX) e detalhes específicos.

- **Tabela `Pedido_has_Pagamento`:**
  - Relaciona pedidos com pagamentos, permitindo que um pedido tenha várias formas de pagamento associadas.

---

### **7. Entrega**
O sistema de entrega é vinculado diretamente aos pedidos, permitindo rastreamento e gerenciamento detalhado do processo de envio.

- **Tabela `Entrega`:**
  - Contém informações como código de rastreio, status da entrega, e datas de envio e entrega.
  - Relaciona-se com a tabela `Pedido` para vincular uma ou mais entregas aos pedidos.

---

### **Relacionamentos Principais**
- **Clientes e Pedidos:**
  - Cada cliente pode fazer múltiplos pedidos, mas um pedido pertence a apenas um cliente.

- **Pedidos e Produtos:**
  - Um pedido pode conter múltiplos produtos, e cada produto pode estar em múltiplos pedidos.

- **Pedidos e Pagamentos:**
  - Cada pedido pode ter várias formas de pagamento associadas.

- **Pedidos e Entregas:**
  - Um pedido pode ter uma ou mais entregas associadas, permitindo rastrear envios fragmentados.

- **Produtos e Estoque:**
  - Um produto pode estar armazenado em múltiplos locais, e um local pode conter múltiplos produtos.

---

### **Finalidade do Projeto**
Este esquema lógico foi desenvolvido para atender às necessidades de um sistema de e-commerce robusto, garantindo:
1. **Escalabilidade:** Suporte para múltiplos clientes, produtos, pedidos, e formas de pagamento.
2. **Flexibilidade:** Capacidade de lidar com produtos de fornecedores próprios e terceiros.
3. **Rastreamento Completo:** Controle detalhado de pedidos, pagamentos, e entregas.
4. **Segregação de Dados:** Gerenciamento específico para clientes PF e PJ.

---
