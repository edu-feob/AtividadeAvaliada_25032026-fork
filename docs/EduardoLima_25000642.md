# Avaliação — Engenharia de Software
**Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante**

Aluno: Eduardo Henrique Nascimento de Lima 

RA: 25000642  

Data: 25 de março de 2026  

---

# 1. Definição do MVP
Descreva aqui **qual parte do sistema** foi incluída no seu MVP.  
Explique claramente:

- O que está **dentro** do MVP  
- O que está **fora** do MVP  
- Por que você fez essas escolhas  

Exemplo de início:  
> “Meu MVP cobre o processo de venda desde a identificação/cadastro do cliente até a emissão do comprovante, incluindo tratamento de estoque insuficiente.”

---

# 2. Regras de Negócio (mínimo: 5)
Liste e descreva **cada RN** de forma clara.

**RN01 — Produto sem estoque não pode estar disponível para venda**  
**RN02 — Um produto controlado só pode ser vendido com devida apresentação da receita médica**  
**RN03 — A administração do estoque, tanto transferência quanto ajuste, deve ser feito por um Gerente**  
**RN04 — Desconto de produtos devem ser adicionados por um Gerente**  
**RN05 — O produto deve ser alertado quando tiver um estoque abaixo do mínimo**

---

# 3. Requisitos Funcionais (mínimo: 8)
Liste os requisitos funcionais do seu MVP.

**RF01 — Cadastro e consulta de produtos**  
**RF02 — Cadastro de cliente**  
**RF03 — Cadastro de produtos**  
**RF04 — Gerar relatórios e indicadores dos produtos**  
**RF05 — Lançamento das Contas a Pagar**  
**RF06 — Lançamento das Contas a Receber**  
**RF07 — Controle de acesso dos usuários**  
**RF08 — Emissão de comprovante após alguma compra**  

---

# 🛡 4. Requisitos Não Funcionais (mínimo: 4)
Liste os RNFs do sistema conforme seu MVP.

**RNF01 — Disponibilidade (O sistema deve estar a maioria do tempo disponível para evitar prejuízos)**  
**RNF02 — Segurança (Todos os acessos e informações de dados dos clientes devem ser restritamente cobertos e criptografados, evitando perda ou roubo de dados)**  
**RNF03 — Usabilidade (O sistema deve ser de fácil acesso e uso, também pensamos em novos funcionários da farmácia)**  
**RNF04 — Escabilidade (O sistema deve suportar uma grande de quantidade de usuários simultâneos)**  

---

# 5. Casos de Uso (mínimo: 10)
### Inserir **diagrama de casos de uso geral**, demonstrando claramente:
- os 10 casos
- relação entre eles e atores
- pelo menos 3 includes
- pelo menos 3 extends

---

# 6. Documentação dos Casos de Uso
Para **cada caso de uso**, utilize o template abaixo:
---

## **UCXX — Nome do Caso de Uso**
**Ator(es):**  
**Descrição:**  
**Pré-condições:**  
**Pós-condições:**  

### Fluxo Principal
1.  
2.  
3.  
4.  

### Fluxos Alternativos / Exceções
- FA01 —  
- FA02 —  

### Relacionamentos
- **Include:** (listar quando aplicável)  
- **Extend:** (listar quando aplicável)  

### Inserir o diagrama de atividades do Caso de Uso, demonstrando tudo o fluxo princial e alternativos/exceções.
> Repita essa estrutura para **todos os seus casos de uso** (mínimo 10).
----------------------------------------------------------------------------------------------------------------------------------------------

## **UC01 — Realizar uma venda**
**Ator(es): Atendente**  
**Descrição: Venda de um produto para o cliente**  
**Pré-condições: Produto que tenha cadastro e estoque disponível**  
**Pós-condições: Realização da venda, atualizando o seu estoque**  

### Fluxo Principal
1. Atendente pesquisa o produto  
2. Sistema retorna o produto 
3. Atendente informa a quantidade desejada  
4. Sistema verifica o estoque disponível
5. Sistema identifica o cliente 

### Fluxos Alternativos / Exceções
- FA01 —  Estoque insuficiente - informa ao atendente
- FA02 — Vendas a prazo

### Relacionamentos
- **Include: UC02, UC03**  
- **Extend: UC04** 

---

## **UC02 — Verificar o estoque**
**Ator(es): Atendente**  
**Descrição: Verifica o estoque no sistema**  
**Pré-condições: Produto que está sendo incluido na venda**  
**Pós-condições: O sistema confirma a disponibilidade do estoque**  

### Fluxo Principal
1. Atendente verifica o estoque do produto  
2. Sistema devolve a disponibilidade do estoque, informando um alerta caso quantidade abaixo do mínimo
3. Atendente continua ou nega a venda ao cliente   

### Fluxos Alternativos / Exceções
- FA01 —  Quantidade não suficiente para a venda

### Relacionamentos
- **Include:**  
- **Extend:**

---

## **UC03 — Identificar o cliente no sistema**
**Ator(es): Atendente**  
**Descrição: Identifica o cliente no sistema**  
**Pré-condições: Uma venda que esteja sendo realizada**  
**Pós-condições: Cliente com vínculo com a venda**  

### Fluxo Principal
1. Durante a venda, o atendente identifica o cliente
2. Informa o CPF ou o nome do cliente no sistema
3. O sistema busca o cadastro
4. Sistema víncula o cliente na venda   

### Fluxos Alternativos / Exceções
- FA01 —  O cliente não foi encontrado no Sistema

### Relacionamentos
- **Include:**  
- **Extend: UC05**

---

## **UC04 — Registro das contas a receber**
**Ator(es): Financeiro**  
**Descrição: Registra as vendas com pagamentos a prazo**  
**Pré-condições: Venda realizada de forma a prazo**  
**Pós-condições: É aberta com Status "Aberta" e com a devida Data de Vencimento**  

### Fluxo Principal
1. O Financeiro recebe a venda a prazo  
2. Após receber, gera uma data para lançar o valor, com sua devida data de vencimento
3. Abre o Status de forma "Aberta"

### Fluxos Alternativos / Exceções
- FA01 —  Cliente com cadastro incompleto não consegue realizar a prazo

### Relacionamentos
- **Include:**  
- **Extend:**

---

## **UC05 — Realizar o Cadastro dos clientes**
**Ator(es): Atendente**  
**Descrição: Cadastrar o cliente caso nao for identificado**  
**Pré-condições: Cliente não identificado na UC03**  
**Pós-condições: O cliente passa a ser identificado quando realizar alguma compra**  

### Fluxo Principal
1. Atendente acessa a página do cadastro de cliente dentro do sistema  
2. Ele informa o Nome, CPF e outros dados importantes
3. Sistema retorna sucesso e cliente passa a ser identificado  

### Fluxos Alternativos / Exceções
- FA01 —  CPF já registrado - cadastro de cliente é barrada pelo sistema

### Relacionamentos
- **Include:**  
- **Extend:**

---

## **UC06 — Registro de compra de um fornecedor**
**Ator(es): Gerente**  
**Descrição: Registrar a compra de um produto de um fornecedor**  
**Pré-condições: Fornecedor e produto já registrado no sistema**  
**Pós-condições: Registro feito e estoque atualizado automaticamente**  

### Fluxo Principal
1. Gerente vai informar o Fornecedor, a quantidade, a data que foi registrado e o valor total
2. Sistema vai registrar a compra
3. O estoque vai ser atualizado
4. O Financeiro verifica a devida condição de pagamento

### Fluxos Alternativos / Exceções
- FA01 —  Compras a prazo

### Relacionamentos
- **Include: UC07**  
- **Extend: UC08**

---

## **UC07 — Atualização do estoque**
**Ator(es): Gerente**  
**Descrição: Atualizar o estoque após algum registro de compra**  
**Pré-condições: Devido registro de compra de produto**  
**Pós-condições: Estoque é atualizado e com valores coerentes**  

### Fluxo Principal
1. Após realizar o registro do produto, o gerente já informa as mudanças pro sistema
2. O sistema já adiciona ou diminui a quantidade do estoque automaticamente

### Fluxos Alternativos / Exceções
- FA01 —  informa para o gerente em forma de alerta caso o estoque tiver abaixo do mínimo

### Relacionamentos
- **Include:**  
- **Extend:**

---

## **UC08 — Lançamento das contas a pagar**
**Ator(es): Financeiro**  
**Descrição: Lançar os produtos com pagamentos a prazo**  
**Pré-condições: Compras com registro de pagamentos a prazo**  
**Pós-condições: Criado o Status de "Aberto" e com sua devida data de vencimento**  

### Fluxo Principal
1. O Financeiro vai identificar a conta que é a prazo
2. Vai gerar o seu devido valor, o seu fornecedor e data de vencimento
3. O status vai ser definido como "Aberto"

### Fluxos Alternativos / Exceções
- FA01 —  Caso o valor for invalido, o Financeiro avisa ao sistema para cancelar o Lançamento

### Relacionamentos
- **Include:**  
- **Extend:**

---

## **UC09 — Consultar os relatórios gerados**
**Ator(es): Gerente, Financeiro ou o Administrador**  
**Descrição: Criação de relatório e consulta de vendas, registro de produtos, etcw**  
**Pré-condições: Usuário com a devida permissão gerar o relatório**  
**Pós-condições: Relatório disponível para consulta**  

### Fluxo Principal
1. Os usuários permitidos seleciona o tipo de relatório que deseja visualizar
2. O sistema vai processar os dados selecionados pelos usuários permitidos
3. O usuário exporta o relatório

### Fluxos Alternativos / Exceções
- FA01 —  Caso não houver dados disponíveis, o sistema gera uma alerta

### Relacionamentos
- **Include:**  
- **Extend:**

---

## **UC10 — Gerenciar os usuários e as devidas permissões**
**Ator(es): Administrador**  
**Descrição: Gerenciar o que o usuário pode fazer no sistema**  
**Pré-condições: Ser um usuário Administrador**  
**Pós-condições: Usuário foi criado e com suas devidas permissões definidas**  

### Fluxo Principal
1. Com administrador logado, ele acessa o painel para a criação e gerenciamento de usuários
2. ele cria, edita ou desativa um usuario
3. define o devido perfil, podendo ser Atendente, Gerente, Financeiro, etc
4. O sistema aplica as devidas permissões definidas

### Fluxos Alternativos / Exceções
- FA01 —  Caso excluir o único administrador que esteja ativo, o sistema impede

### Relacionamentos
- **Include:**  
- **Extend:**
