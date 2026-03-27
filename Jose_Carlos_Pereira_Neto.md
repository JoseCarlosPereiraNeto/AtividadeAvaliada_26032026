## 1. Definição do MVP

**O que está DENTRO do MVP**:
- **Venda Direta (PDV):** Registro de vendas à vista e a prazo, com pesquisa de produtos por nome ou código de barras.
- **Gestão de Estoque Automatizada:** Atualização em tempo real (baixa na venda e entrada na compra) para evitar divergências.
- **Cadastro Simplificado:** Registro de produtos (descrição, preço, fabricante) e clientes (dados básicos para histórico e vendas a prazo).
- **Módulo de Compras Básico:** Registro de entrada de mercadorias por fornecedor para alimentar o estoque.
- **Financeiro Essencial:** Lançamento automático em Contas a Receber (vendas a prazo) e Contas a Pagar (compras de fornecedores), com controle de status (Aberto/Pago).
- **Relatórios Críticos:** Indicadores de "Posição de Estoque por Unidade" e "Vendas Totais Diárias".
- **Perfis de Acesso:** Diferenciação básica entre Atendente (vendas) e Gerente (estoque/compras).

**O que está FORA do MVP**:
- **Módulo de Farmacêutico:** Validação de receitas e controle de medicamentos retidos (SNGPC) para a V2.
- **Transferências entre Unidades:** Gestão de estoque isolada por unidade nesta fase.
- **Alertas de Nível Mínimo:** Notificações proativas de estoque baixo.
- **Relatórios Estratégicos Complexos:** "Produtos nunca vendidos" ou "Auditorias de Desempenho".
- **Integração com Convênios Externos:** Apenas venda a prazo interna (sem webservices de planos de saúde).
- **Gestão de Perdas e Devoluções:** Ajustes manuais de inventário.

**Por que essas escolhas foram feitas**:
A prioridade é estancar a perda de informação e corrigir a divergência de estoque e falhas financeiras.
- **Foco na Integridade:** Automação Estoque <-> Venda <-> Financeiro para eliminar erros manuais.
- **Agilidade no Balcão:** Cadastro rápido e busca eficiente para não prejudicar o atendimento.
- **Redução de Complexidade:** Adiar validações sanitárias complexas para estabilizar a base do sistema primeiro.

---

## 2. Regras de Negócio

- **RN01**  Bloqueio de Estoque | Não se vende o que não tem em estoque físico. |
- **RN02**  Venda a Prazo = Dívida | Toda venda a prazo gera obrigatoriamente um "Contas a Receber". |
- **RN03**  Entrada Automática | Ao confirmar compra do fornecedor, o estoque sobe e o "Contas a Pagar" é gerado. |
- **RN04**  Hierarquia de Acesso | Atendente realiza vendas; Gerente altera preços e estoque. |
- **RN05**  Trava de Segurança | Medicamentos controlados exigem liberação do Farmacêutico (conforme a lei). |

---

## 3. Requisitos Funcionais

- **RF01 - Registrar Venda:** Permitir vendas de produtos por nome/código de barras com baixa automática de estoque.
- **RF02 - Consultar Estoque:** Consulta em tempo real da quantidade disponível por unidade.
- **RF03 - Gerenciar Cadastro de Clientes:** Cadastrar novos clientes e consultar histórico para vendas a prazo.
- **RF04 - Registrar Entrada de Mercadoria:** Lançamento de compras, atualização de estoque e geração de títulos financeiros.
- **RF05 - Gerar Contas a Receber:** Registro automático de conta a receber para vendas na modalidade "A Prazo".
- **RF06 - Autorizar Medicamentos Controlados:** Exigir validação do perfil Farmacêutico e registro da receita.
- **RF07 - Consultar Contas a Pagar:** Acompanhamento de débitos com fornecedores e despesas da unidade.
- **RF08 - Gerar Relatórios de Vendas:** Emissão de totais por período (dia/semana/mês).

---

## 4. Requisitos Não Funcionais

- **RNF01 - Segurança de Dados:** Acesso funcional restrito conforme o perfil do usuário (Atendente, Farmacêutico, Gerente).
- **RNF02 - Disponibilidade:** Operação 24/7 com o mínimo de interrupções.
- **RNF03 - Desempenho de Venda:** Consulta e finalização de venda em no máximo 3 segundos.
- **RNF04 - Integridade de Dados:** Consistência de informações entre unidades; baixa de uma unidade não afeta o saldo de outra.

---

## 5. Casos de Uso

**UC01 - Realizar Venda:** O processo principal do balcão.  
**UC02 - Consultar Estoque:** Verificação de disponibilidade.  
**UC03 - Identificar Cliente:** Busca ou cadastro rápido.  
<img width="424" height="130" alt="image" src="https://github.com/user-attachments/assets/6c27ed2c-eb96-45f6-9816-424fc60ca1ea" />

**UC04 - Validar Receita:** Conferência técnica do farmacêutico.  
<img width="399" height="127" alt="image" src="https://github.com/user-attachments/assets/8f01a388-8446-4dd5-935a-c0e70db31b5b" />

**UC05 - Registrar Venda a Prazo:** Criação do débito para o cliente.  
<img width="329" height="228" alt="image" src="https://github.com/user-attachments/assets/cdbcd354-efde-4369-8cc0-781d36f41180" />

**UC06 - Manter Produtos:** Cadastro e edição de itens.  
<img width="173" height="133" alt="image" src="https://github.com/user-attachments/assets/f5ec6aae-4c4f-4fa0-a217-6fd71fc5bef0" />

**UC07 - Registrar Compra:** Entrada de NF de fornecedores.  
**UC08 - Gerar Contas a Pagar:** Lançamento automático de dívida com fornecedor.  
<img width="168" height="207" alt="image" src="https://github.com/user-attachments/assets/dd1c201d-bde6-4920-8839-f24e2e73c81f" />

**UC09 - Baixar Título:** Registro de pagamento/recebimento efetuado.  
<img width="155" height="127" alt="image" src="https://github.com/user-attachments/assets/434d31e3-6ce0-4e3b-9f17-ba6f8a10ee43" />

**UC10 - Gerar Relatórios:** Visão gerencial da matriz.  
<img width="273" height="125" alt="image" src="https://github.com/user-attachments/assets/a2da1e12-dfb6-42aa-91bb-b1de2ca68b9d" />

---

# 6. Documentação dos Casos de Uso

---

**UC01 — Realizar Venda**
* **Ator(es):** Atendente.
* **Descrição:** Registrar a saída de produtos para um cliente, processando o pagamento e baixando o estoque em tempo real.
* **Pré-condições:** Usuário logado; produtos com estoque disponível na unidade.
* **Pós-condições:** Estoque atualizado; comprovante emitido; registro financeiro criado.
* **Fluxo Principal:**
    1. O atendente inicia uma nova venda no PDV.
    2. O atendente consulta e adiciona produtos (**UC02**).
    3. O sistema calcula o valor total da venda e impostos.
    4. O atendente seleciona a forma de pagamento (Dinheiro, Cartão ou Prazo).
    5. O sistema registra a operação e emite o comprovante fiscal.
* **Fluxos Alternativos / Exceções:**
    * **FA01 — Produto Controlado:** Se houver item controlado, exige validação do farmacêutico (**UC04**).
    * **FA02 — Venda a Prazo:** Se o pagamento for a prazo, exige identificação do cliente (**UC05**).
* **Relacionamentos:**
    * **Include:** UC02.
    * **Extend:** UC03, UC04, UC05.

---

**UC02 — Consultar Estoque**
* **Ator(es):** Atendente, Gerente.
* **Descrição:** Verificar a disponibilidade física e o preço unitário de um produto no sistema.
* **Pré-condições:** Produto deve estar previamente cadastrado.
* **Pós-condições:** Informações de saldo e preço exibidas em tela.
* **Fluxo Principal:**
    1. O usuário informa o nome, código interno ou código de barras.
    2. O sistema busca o saldo disponível na unidade local.
    3. O sistema exibe a quantidade e localização no estoque.
* **Fluxos Alternativos / Exceções:**
    * **FA01 — Estoque Zerado:** O sistema emite um alerta visual de que o item está indisponível para venda.
* **Relacionamentos:**
    * **Include:** Nenhum.
    * **Extend:** Nenhum.

---

**UC03 — Identificar Cliente**
* **Ator(es):** Atendente.
* **Descrição:** Localizar um cliente existente ou realizar um cadastro rápido para histórico ou venda a prazo.
* **Pré-condições:** Acesso ao módulo de clientes.
* **Pós-condições:** Cliente vinculado à transação de venda atual.
* **Fluxo Principal:**
    1. O atendente solicita o CPF ou nome do cliente.
    2. O sistema realiza a busca na base centralizada.
    3. O atendente confirma os dados exibidos.
* **Fluxos Alternativos / Exceções:**
    * **FA01 — Cliente não encontrado:** O atendente realiza o cadastro imediato com dados mínimos (Nome e CPF).
* **Relacionamentos:**
    * **Include:** Nenhum.
    * **Extend:** UC01.

---

**UC04 — Validar Receita Médica**
* **Ator(es):** Farmacêutico.
* **Descrição:** Autorizar tecnicamente a venda de medicamentos que exigem retenção de receita (controlados).
* **Pré-condições:** Item com flag "controlado" adicionado ao carrinho de vendas.
* **Pós-condições:** Venda liberada para processamento financeiro.
* **Fluxo Principal:**
    1. O farmacêutico acessa a tela de autorização de venda.
    2. Registra os dados do médico prescritor (CRM) e data da receita.
    3. O farmacêutico confirma a autorização via senha ou digital.
* **Fluxos Alternativos / Exceções:**
    * **FA01 — Receita Vencida/Inválida:** O farmacêutico nega a venda e o item é removido do carrinho.
* **Relacionamentos:**
    * **Include:** Nenhum.
    * **Extend:** UC01.

---

**UC05 — Registrar Venda a Prazo**
* **Ator(es):** Atendente.
* **Descrição:** Criar um título de débito vinculado ao cliente para pagamento em data futura (convênio/crediário).
* **Pré-condições:** Cliente obrigatoriamente identificado (**UC03**).
* **Pós-condições:** Título gerado no módulo de Contas a Receber.
* **Fluxo Principal:**
    1. O sistema solicita a confirmação do cliente vinculado.
    2. O sistema verifica o histórico de crédito e inadimplência.
    3. O sistema gera as parcelas e define a data de vencimento.
* **Fluxos Alternativos / Exceções:**
    * **FA01 — Bloqueio Financeiro:** O sistema impede a venda se o cliente possuir parcelas em atraso acima do limite permitido.
* **Relacionamentos:**
    * **Include:** UC03.
    * **Extend:** UC01.

---

**UC06 — Manter Cadastro de Produtos**
* **Ator(es):** Gerente.
* **Descrição:** Administrar o catálogo de produtos da rede (inclusão, edição e inativação).
* **Pré-condições:** Autenticação com perfil de nível Gerencial.
* **Pós-condições:** Informações do produto replicadas para as unidades.
* **Fluxo Principal:**
    1. O gerente acessa o menu de cadastro de produtos.
    2. Insere/altera descrição, preço de venda, fabricante e unidade de medida.
    3. O sistema salva os dados e atualiza o catálogo central.
* **Fluxos Alternativos / Exceções:**
    * **FA01 — Código EAN Existente:** O sistema impede a criação de duplicidade se o código de barras já estiver em uso.
* **Relacionamentos:**
    * **Include:** Nenhum.
    * **Extend:** Nenhum.

---

**UC07 — Registrar Compra (Entrada)**
* **Ator(es):** Gerente.
* **Descrição:** Registrar a entrada de mercadorias no estoque e gerar a obrigação financeira correspondente.
* **Pré-condições:** Fornecedor cadastrado; Nota Fiscal recebida fisicamente.
* **Pós-condições:** Saldo de estoque incrementado; Contas a Pagar gerado automaticamente.
* **Fluxo Principal:**
    1. O gerente seleciona o fornecedor e insere o número da NF.
    2. Registra os itens e quantidades que deram entrada na unidade.
    3. O sistema atualiza o estoque e invoca a geração financeira (**UC08**).
* **Fluxos Alternativos / Exceções:**
    * **FA01 — Margem de Lucro Baixa:** O sistema alerta se o novo custo de compra inviabilizar a margem de lucro atual.
* **Relacionamentos:**
    * **Include:** UC08.
    * **Extend:** Nenhum.

---

**UC08 — Gerar Contas a Pagar**
* **Ator(es):** Sistema (Automático).
* **Descrição:** Criar automaticamente registros de dívidas com fornecedores a partir de compras realizadas.
* **Pré-condições:** Conclusão do registro de entrada (**UC07**).
* **Pós-condições:** Título financeiro disponível para o setor administrativo.
* **Fluxo Principal:**
    1. O sistema captura o valor total, parcelas e prazos da NF de entrada.
    2. Cria um registro no módulo de Contas a Pagar com status "Aberto".
* **Fluxos Alternativos / Exceções:**
    * **FA01 — Compra à Vista:** Caso marcado como pagamento imediato, o título é gerado com status "Pago".
* **Relacionamentos:**
    * **Include:** Nenhum (Invocado pelo UC07).
    * **Extend:** Nenhum.

---

**UC09 — Baixar Título Financeiro**
* **Ator(es):** Financeiro.
* **Descrição:** Registrar a quitação de débitos (pagar fornecedores) ou créditos (receber de clientes).
* **Pré-condições:** Título existente com status "Aberto" ou "Atrasado".
* **Pós-condições:** Status do título atualizado para "Liquidado" ou "Recebido".
* **Fluxo Principal:**
    1. O operador financeiro filtra os títulos pendentes por período ou nome.
    2. Confirma o valor efetivamente pago/recebido (com juros ou descontos).
    3. O sistema altera o status e registra o log da transação.
* **Fluxos Alternativos / Exceções:**
    * **FA01 — Estorno:** Permite reverter uma baixa caso tenha sido feita por erro operacional.
* **Relacionamentos:**
    * **Include:** Nenhum.
    * **Extend:** Nenhum.

---

**UC10 — Gerar Relatórios de Desempenho**
* **Ator(es):** Gerente, Financeiro.
* **Descrição:** Gerar documentos de análise sobre vendas, estoque e fluxo de caixa.
* **Pré-condições:** Existência de transações no banco de dados para o período.
* **Pós-condições:** Relatório gerado em tela ou arquivo (PDF/XLS).
* **Fluxo Principal:**
    1. O usuário seleciona o modelo de relatório (ex: Curva ABC de Produtos).
    2. Aplica filtros de data, unidade física e categoria de produto.
    3. O sistema compila os dados e apresenta os indicadores.
* **Fluxos Alternativos / Exceções:**
    * **FA01 — Dados Insuficientes:** O sistema informa se o período selecionado não possui registros.
* **Relacionamentos:**
    * **Include:** Nenhum.
    * **Extend:** Nenhum.
