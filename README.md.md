# Entrega 1 — Modelo Conceitual (DER)
### Modelagem de um sistema de gestão de informações para uma organização de pequeno porte

**Grupo:** Arthur Marques, Caue Soares, Caroline Nogueira

**RGM:** Arthur Marques — 04711793-1 · Caue Soares — 47207094 · Caroline Nogueira — 47031867

---

# Modelagem de Banco de Dados para a LaSabore

## Introdução

A LaSabore é uma organização de pequeno porte do segmento alimentício que utiliza recursos digitais para o recebimento e gerenciamento de pedidos. Durante o levantamento realizado com a organização, foram identificadas dificuldades relacionadas à organização e ao acompanhamento dos pedidos, principalmente porque os pedidos são realizados de forma digital e não há um atendente responsável por registrar diretamente o pedido com o cliente.

O objetivo deste trabalho é propor um modelo conceitual de banco de dados capaz de centralizar, organizar e relacionar as informações de clientes, pedidos, produtos, ingredientes, estoque, pagamentos, produção e entregas.

A delimitação desta primeira entrega é o **núcleo do ciclo pedido → produção → pagamento → entrega/retirada**, contemplando também o cadastro de clientes, produtos, categorias, ingredientes, usuários e controle de estoque.

## Desenvolvimento

### Caracterização da Organização

- **Nome e natureza da organização:** LaSabore — organização de pequeno porte do segmento alimentício, com utilização de recursos digitais para recebimento e gerenciamento de pedidos.
- **Contexto e porte:** a organização possui aproximadamente 10 funcionários e utiliza processos digitais para o recebimento de pedidos.
- **Problemas e necessidades identificados:** foram identificadas dificuldades relacionadas à organização e ao acompanhamento dos pedidos. Os pedidos são realizados de forma digital, sem um atendente responsável por registrar o pedido diretamente com o cliente. Existe, portanto, necessidade de centralizar as informações e acompanhar melhor as etapas do pedido.
- **Justificativa da escolha:** a LaSabore foi escolhida por apresentar processos de negócio que podem ser representados por um modelo conceitual de dados, envolvendo clientes, pedidos, produtos, ingredientes, estoque, pagamentos, produção e entregas.
- **Evidências da organização:** a organização foi analisada a partir de entrevista e informações fornecidas pelo grupo, além do registro fotográfico da organização.

**Dados da organização:**

| Informação | Dado |
|---|---|
| Organização | LaSabore |
| Endereço | Rua Antonio Soares Pais, nº 589 — CEP 08460-500 |
| Telefone | (11) 2362-6127 / (11) 96711-9478 |
| Funcionários | 10 |
| Entrevistado | Tanilo Marques Amorim Rocha |

---

### Processos de Negócio

**Principais processos mapeados:**

1. *Cadastro de cliente* — registro e manutenção dos dados dos clientes.
2. *Registro do pedido* — criação do pedido, seleção dos produtos, quantidades e observações.
3. *Organização dos itens* — relacionamento entre pedido, produtos e quantidades.
4. *Produção* — acompanhamento das etapas de preparação do pedido.
5. *Controle de estoque* — registro das movimentações de ingredientes.
6. *Pagamento* — registro do método, valor e situação do pagamento.
7. *Entrega/retirada* — acompanhamento da entrega quando aplicável.
8. *Atualização do status* — acompanhamento da situação do pedido.

**Fluxo principal, em texto:**

```text
Cliente
   → Pedido é registrado
      → Produtos e quantidades são definidos
         → Pedido segue para produção
            ├─ Ingredientes são utilizados
            ├─ Estoque é movimentado
            ├─ Pagamento é registrado
            └─ Entrega/retirada é acompanhada
               → Pedido é concluído
```

---

### Requisitos Funcionais

#### RF01 – Cadastrar clientes

O sistema deve permitir o cadastro, consulta e atualização dos dados dos clientes.

**Especificações:**

- Cadastrar nome;
- Telefone;
- E-mail;
- Endereço;
- Número;
- Complemento;
- Bairro;
- Cidade;
- Observações;
- Permitir consultar clientes cadastrados;
- Permitir alterar dados existentes.

---

#### RF02 – Registrar pedidos

O sistema deve permitir registrar pedidos e seus respectivos itens.

**Especificações:**

- Identificar o cliente;
- Identificar o usuário responsável;
- Registrar data e hora;
- Registrar canal de origem;
- Adicionar produtos;
- Informar quantidades;
- Registrar observações;
- Calcular subtotal;
- Aplicar desconto quando necessário;
- Registrar taxa de entrega;
- Calcular o valor total;
- Controlar o status do pedido.

**Status possíveis:**

- Novo;
- Confirmado;
- Em preparo;
- Pronto;
- Saiu para entrega;
- Entregue;
- Cancelado.

---

#### RF03 – Cadastrar produtos e categorias

O sistema deve permitir cadastrar e gerenciar produtos e suas categorias.

**Especificações:**

- Código do produto;
- Categoria;
- Nome;
- Descrição;
- Preço de venda;
- Custo;
- Status ativo/inativo;
- Cadastro e atualização de categorias.

---

#### RF04 – Relacionar produtos e ingredientes

O sistema deve permitir relacionar os produtos aos ingredientes utilizados em sua composição.

**Especificações:**

- Identificar o produto;
- Identificar o ingrediente;
- Informar a quantidade utilizada;
- Manter a ficha técnica do produto.

Um produto poderá utilizar vários ingredientes, e um ingrediente poderá participar da composição de vários produtos.

---

#### RF05 – Controlar estoque

O sistema deve permitir registrar e acompanhar as movimentações de estoque dos ingredientes.

**Especificações:**

- Identificar o ingrediente;
- Identificar o usuário responsável;
- Registrar tipo de movimentação;
- Informar quantidade;
- Registrar motivo;
- Registrar data e hora;
- Permitir consultar o histórico de movimentações;
- Manter quantidade em estoque e estoque mínimo.

**Tipos de movimentação:**

- Entrada;
- Saída;
- Ajuste.

---

#### RF06 – Registrar pagamentos

O sistema deve permitir registrar os pagamentos associados aos pedidos.

**Especificações:**

- Identificar o pedido;
- Registrar método de pagamento;
- Registrar valor;
- Registrar status;
- Registrar data e hora da operação.

**Status possíveis:**

- Pendente;
- Pago;
- Cancelado;
- Estornado.

---

#### RF07 – Acompanhar produção

O sistema deve permitir acompanhar a preparação dos pedidos.

**Especificações:**

- Identificar o pedido;
- Registrar prioridade;
- Registrar etapa atual;
- Registrar status;
- Registrar início;
- Registrar fim.

**Status possíveis:**

- Aguardando;
- Em preparo;
- Pronto;
- Finalizado.

---

#### RF08 – Registrar e acompanhar entregas

O sistema deve permitir registrar e acompanhar as entregas quando houver entrega associada ao pedido.

**Especificações:**

- Identificar o pedido;
- Registrar entregador;
- Registrar endereço de entrega;
- Registrar status;
- Registrar horário de saída;
- Registrar horário de entrega.

**Status possíveis:**

- Aguardando;
- Em rota;
- Entregue;
- Cancelada.

---

#### RF09 – Gerenciar usuários

O sistema deve permitir gerenciar os usuários que utilizam o sistema.

**Especificações:**

- Identificador do usuário;
- Nome;
- E-mail;
- Senha armazenada de forma protegida;
- Cargo;
- Status ativo/inativo;
- Data de criação.

---

#### RF10 – Consultar informações

O sistema deve permitir pesquisar e consultar as informações armazenadas.

A pesquisa deverá permitir filtros por:

- Cliente;
- Pedido;
- Produto;
- Categoria;
- Ingrediente;
- Pagamento;
- Produção;
- Entrega;
- Status;
- Período.

---

### Requisitos Não Funcionais

#### RNF01 – Segurança

O sistema deve proteger as informações armazenadas e controlar o acesso de acordo com o perfil do usuário.

**Especificações:**

- Login e senha;
- Senhas armazenadas de forma segura;
- Controle de acesso;
- Bloqueio de usuários não autorizados;
- Proteção das informações de clientes, pedidos e pagamentos.

---

#### RNF02 – Desempenho

O sistema deve apresentar desempenho adequado ao porte da organização.

**Especificações:**

- Consultas comuns devem apresentar resultados rapidamente;
- O banco deve possuir estrutura organizada;
- O sistema deve continuar adequado com o crescimento da quantidade de registros.

---

#### RNF03 – Usabilidade

A interface deve ser clara, organizada e fácil de utilizar.

**Especificações:**

- Menus organizados;
- Campos identificados claramente;
- Formulários padronizados;
- Mensagens de erro compreensíveis;
- Navegação simples.

---

#### RNF04 – Integridade dos dados

O sistema deve garantir que os dados armazenados sejam corretos, completos e consistentes.

**Especificações:**

- Utilizar chaves primárias e estrangeiras;
- Validar campos obrigatórios;
- Evitar registros duplicados quando aplicável;
- Impedir relacionamentos inexistentes;
- Manter consistência entre pedidos, clientes, produtos, pagamentos e demais entidades.

---

#### RNF05 – Disponibilidade

O sistema deve estar disponível durante o período de funcionamento da organização.

**Especificações:**

- Manter o sistema acessível durante o horário de trabalho;
- Registrar erros críticos;
- Permitir recuperação das informações em caso de falha.

---

### Regras de Negócio

- **Regras operacionais:**
  - Um cliente pode possuir vários pedidos; cada pedido está associado a um cliente.
  - Todo pedido deve possuir pelo menos um item.
  - Cada item do pedido referencia um produto cadastrado.
  - Um produto pode aparecer em vários pedidos.
  - Produtos e ingredientes possuem relação N:N representada pela ficha técnica.
  - Movimentações de estoque registram ingrediente, tipo, quantidade e data/hora.
  - O pedido possui status para acompanhamento.
  - Pedidos cancelados não avançam para as etapas posteriores.
  - Uma entrega é associada ao pedido quando houver entrega.
  - O pagamento deve estar associado ao pedido correspondente.
  - A produção acompanha a preparação do pedido.

- **Restrições organizacionais:**
  - As informações de cadastro, pedido, produção, estoque, pagamento e entrega devem permanecer separadas no modelo.
  - Os exemplos utilizados no dicionário de dados são fictícios e não representam dados pessoais reais.
  - O modelo deve permitir evolução futura conforme novas necessidades da organização.

---

### Dicionário de Dados Conceitual (Preliminar)

O Dicionário de Dados completo está disponível no arquivo **Dicionario_de_Dados_LaSabore.html**.

As entidades contempladas são:

- **USUÁRIO**
- **CLIENTE**
- **CATEGORIA**
- **PRODUTO**
- **INGREDIENTE**
- **FICHA TÉCNICA**
- **PEDIDO**
- **ITEM DO PEDIDO**
- **PAGAMENTO**
- **PRODUÇÃO**
- **ENTREGA**
- **MOVIMENTAÇÃO DE ESTOQUE**

O dicionário apresenta os atributos, descrições e regras de negócio associadas a cada entidade.

---

### Modelagem Conceitual (Entidades, Atributos, Relacionamentos)

**Entidades reconhecidas:** USUÁRIO, CLIENTE, CATEGORIA, PRODUTO, INGREDIENTE, FICHA TÉCNICA, PEDIDO, ITEM DO PEDIDO, PAGAMENTO, PRODUÇÃO, ENTREGA e MOVIMENTAÇÃO DE ESTOQUE.

**Classificação dos atributos:**

Os atributos podem ser identificadores, descritivos, quantitativos, temporais ou de status. Identificadores distinguem ocorrências; descritivos caracterizam entidades; quantitativos representam valores e quantidades; temporais registram eventos; status indicam situações.

**Relacionamentos pertinentes:**

- Um **CLIENTE** pode possuir vários **PEDIDOS**; cada pedido está associado a um cliente.
- Um **PEDIDO** possui um ou mais **ITENS DO PEDIDO**.
- Um **PRODUTO** pode aparecer em vários **ITENS DO PEDIDO**.
- Uma **CATEGORIA** pode agrupar vários **PRODUTOS**.
- **PRODUTO** e **INGREDIENTE** possuem relacionamento N:N por meio da **FICHA TÉCNICA**.
- Um **INGREDIENTE** possui várias **MOVIMENTAÇÕES DE ESTOQUE**.
- Um **USUÁRIO** pode registrar vários **PEDIDOS**.
- Um **PEDIDO** pode possuir registros de **PAGAMENTO**.
- Um **PEDIDO** possui acompanhamento de **PRODUÇÃO**.
- Um **PEDIDO** pode possuir uma **ENTREGA** quando aplicável.
- Um **USUÁRIO** pode registrar várias **MOVIMENTAÇÕES DE ESTOQUE**.

**Cardinalidades principais:**

| Relacionamento | Cardinalidade |
|---|---|
| CLIENTE — PEDIDO | 1:N |
| PEDIDO — ITEM DO PEDIDO | 1:N |
| PRODUTO — ITEM DO PEDIDO | 1:N |
| CATEGORIA — PRODUTO | 1:N |
| PRODUTO — INGREDIENTE | N:N |
| INGREDIENTE — MOVIMENTAÇÃO DE ESTOQUE | 1:N |
| USUÁRIO — PEDIDO | 1:N |
| PEDIDO — PAGAMENTO | 1:N |
| PEDIDO — PRODUÇÃO | 1:1 |
| PEDIDO — ENTREGA | 1:0..1 |
| USUÁRIO — MOVIMENTAÇÃO DE ESTOQUE | 1:N |

---

### Diagrama Entidade-Relacionamento (DER)

![DER - LaSabore](DER_LaSabore.png)

O DER representa as entidades, atributos, relacionamentos e cardinalidades definidos no modelo conceitual.

---

### Justificativa Técnica

A decisão central do modelo foi utilizar **PEDIDO** como entidade central, pois ele conecta o cliente aos produtos solicitados e às etapas posteriores de produção, pagamento e entrega.

A separação de **ITEM DO PEDIDO** permite que um pedido contenha vários produtos, cada um com sua quantidade, preço aplicado e observação, sem duplicar os dados gerais do pedido.

A relação N:N entre **PRODUTO** e **INGREDIENTE** é representada pela **FICHA TÉCNICA**, permitindo registrar quais ingredientes fazem parte da composição de cada produto e qual quantidade é utilizada.

**PRODUÇÃO**, **PAGAMENTO** e **ENTREGA** são entidades próprias porque representam processos distintos relacionados ao pedido. Essa separação facilita o acompanhamento das etapas e evita a repetição de informações.

A entidade **MOVIMENTAÇÃO DE ESTOQUE** permite registrar o histórico das entradas, saídas e ajustes dos ingredientes, mantendo o controle das movimentações separado do cadastro do ingrediente.

As cardinalidades foram definidas com base nas regras de negócio levantadas e devem ser confrontadas com a operação real da organização antes da versão definitiva.

---

### Uso de Inteligência Artificial

A Inteligência Artificial foi utilizada como apoio à estruturação e documentação do projeto, sem substituir o levantamento realizado com a organização.

| Item | O que registrar |
|---|---|
| **Ferramenta e etapa** | ChatGPT, utilizado como apoio na organização e redação do README, requisitos, regras de negócio, dicionário conceitual e justificativa técnica. |
| **Motivação** | Organizar as informações levantadas pelo grupo de acordo com o roteiro da Entrega 1 e auxiliar na documentação do modelo conceitual. |
| **Prompt(s) utilizados** | Solicitações para estruturar o projeto da LaSabore conforme o roteiro de Entrega 1 — Modelo Conceitual (DER), organizar requisitos, regras, dicionário, entidades, relacionamentos, justificativa técnica e documentação do uso de IA. |
| **Resposta recebida** | Estruturação e redação preliminar das seções do README, além de apoio na descrição das entidades, atributos, relacionamentos e regras. |
| **Fontes consultadas e verificadas** | Roteiro da atividade fornecido pelo professor, informações fornecidas pelo grupo a partir da entrevista com Tanilo Marques Amorim Rocha, aplicação LaSabore Gestão como referência do sistema e registro fotográfico fornecido pelo grupo. |
| **Trechos rejeitados ou corrigidos** | O grupo revisou e ajustou informações para manter somente aquilo que corresponde ao processo observado na organização, evitando transformar sugestões genéricas da IA em fatos sobre a empresa. |
| **Justificativa da escolha final** | A versão final foi mantida somente após a revisão das informações pelo grupo e a adequação ao processo real levantado na organização. |
| **Reflexão crítica** | A IA foi utilizada como ferramenta de apoio. A responsabilidade pela validação das informações, regras de negócio, entidades, relacionamentos e decisões finais de modelagem permanece com o grupo. |

---

## Conclusão

Nesta primeira entrega, foi desenvolvido o modelo conceitual de dados da LaSabore, tendo o **PEDIDO** como elemento central do processo. O modelo contempla clientes, produtos, categorias, ingredientes, ficha técnica, produção, pagamentos, entregas, usuários e movimentações de estoque.

A construção do modelo permitiu transformar os processos observados na organização em entidades, atributos, relacionamentos e regras de negócio organizadas. A separação entre pedido, item do pedido, produção, pagamento e entrega também permite acompanhar as diferentes etapas sem concentrar informações distintas em uma única estrutura.

Outro ponto importante foi representar a relação entre produtos e ingredientes por meio da ficha técnica, permitindo que o modelo possa ser utilizado futuramente para apoiar o controle de estoque e a composição dos produtos.

O resultado desta entrega é composto pelo **README.md**, pelo **DER em imagem** e pelo **Dicionário de Dados em HTML**, que devem ser publicados separadamente no repositório GitHub do grupo.

---

## Referências Bibliográficas

HEUSER, Carlos Alberto. **Projeto de Banco de Dados**. 6. ed. Porto Alegre: Bookman, 2009.

ELMASRI, Ramez; NAVATHE, Shamkant B. **Sistemas de Banco de Dados**. 7. ed. São Paulo: Pearson Education do Brasil, 2019.

SILBERSCHATZ, Abraham; KORTH, Henry F.; SUDARSHAN, S. **Sistema de Banco de Dados**. 7. ed. Rio de Janeiro: Grupo GEN, 2020.

DATE, C. J. **Introdução a Sistemas de Bancos de Dados**. 8. ed. Rio de Janeiro: Elsevier, 2003.

---

## Critérios Atitudinais

*(avaliados por Avaliação 360º entre os integrantes do grupo — não é conteúdo deste README)*
