# Mapa de Modelagem — Fluxos

**ESCOLA DE TI 2026**
**[Nome a Definir] — Marketplace de Moda Regional com Delivery**

Versão: 1.0 | Data: Março/2026

---

## Sumário de Fluxos

| #  | Fluxo                                          | Ator Principal      | Escopo   |
|----|-------------------------------------------------|----------------------|----------|
| 01 | Cadastro de Consumidor                          | Consumidor           | MVP      |
| 02 | Cadastro de Lojista                             | Lojista              | MVP      |
| 03 | Cadastro de Entregador                          | Entregador           | MVP      |
| 04 | Login e Autenticação                            | Todos                | MVP      |
| 05 | Recuperação de Senha                            | Todos                | MVP      |
| 06 | Edição de Perfil                                | Todos                | MVP      |
| 07 | Cadastro de Produto                             | Lojista              | MVP      |
| 08 | Edição de Produto                               | Lojista              | MVP      |
| 09 | Exclusão / Desativação de Produto               | Lojista              | MVP      |
| 10 | Busca e Filtragem de Produtos                   | Consumidor           | MVP      |
| 11 | Adicionar Produto ao Carrinho                   | Consumidor           | MVP      |
| 12 | Finalização de Compra (Checkout)                | Consumidor           | MVP      |
| 13 | Recebimento e Confirmação de Pedido             | Lojista              | MVP      |
| 14 | Acompanhamento de Pedido                        | Consumidor           | MVP      |
| 15 | Histórico de Pedidos (Consumidor)               | Consumidor           | MVP      |
| 16 | Histórico de Vendas (Lojista)                   | Lojista              | MVP      |
| 17 | Delivery — Coleta e Entrega                     | Entregador           | Pós-MVP  |
| 18 | Solicitação de Devolução                        | Consumidor           | Pós-MVP  |
| 19 | Processamento da Devolução                      | Entregador / Lojista | Pós-MVP  |
| 20 | Avaliação de Produto / Loja                     | Consumidor           | Pós-MVP  |
| 21 | Chat entre Consumidor e Lojista                 | Consumidor / Lojista | Pós-MVP  |
| 22 | Gestão da Loja (Painel do Lojista)              | Lojista              | Pós-MVP  |
| 23 | Painel Administrativo                           | Administrador        | Pós-MVP  |
| 24 | Configurações do Aplicativo                     | Todos                | MVP      |
| 25 | Logout                                          | Todos                | MVP      |

---

## Fluxos — MVP

---

### 01. Cadastro de Consumidor

Abrir a tela inicial do aplicativo → Selecionar "Criar Conta" → Selecionar tipo de usuário **"Consumidor"** → Preencher dados pessoais (nome completo, CPF, RG, e-mail, senha) → Informar CEP e endereço de entrega → Sistema validar CPF e dados informados → Aceitar os Termos de Uso e Política de Privacidade (LGPD) → Confirmar cadastro → Sistema enviar e-mail de verificação → Consumidor confirmar e-mail → Cadastro ativado com sucesso.

- **Exceções:** CPF já cadastrado; e-mail inválido ou já em uso; CEP não encontrado; campos obrigatórios não preenchidos.

---

### 02. Cadastro de Lojista

Abrir a tela inicial do aplicativo → Selecionar "Criar Conta" → Selecionar tipo de usuário **"Lojista"** → Preencher dados pessoais (nome completo, CPF) → Informar dados da loja (nome da loja, CNPJ, endereço da loja) → Informar dados bancários para recebimento → Sistema validar CNPJ e CPF → Aceitar os Termos de Uso e Política de Privacidade (LGPD) → Confirmar cadastro → Sistema enviar e-mail de verificação → Lojista confirmar e-mail → Cadastro ativado e loja pendente de aprovação pelo administrador.

- **Exceções:** CNPJ inválido ou já cadastrado; CPF já em uso; dados bancários incompletos; endereço inválido.

---

### 03. Cadastro de Entregador

Abrir a tela inicial do aplicativo → Selecionar "Criar Conta" → Selecionar tipo de usuário **"Entregador"** → Preencher dados pessoais (nome completo, CPF, RG) → Informar CNH e dados do veículo (tipo, modelo, placa) → Enviar comprovante de endereço → Sistema validar CPF, RG e CNH → Aceitar os Termos de Uso e Política de Privacidade (LGPD) → Confirmar cadastro → Sistema enviar e-mail de verificação → Entregador confirmar e-mail → Cadastro ativado e perfil pendente de aprovação pelo administrador.

- **Exceções:** CNH inválida ou vencida; CPF já cadastrado; documentos ilegíveis; dados do veículo incompletos.

---

### 04. Login e Autenticação

Abrir a tela inicial do aplicativo → Informar e-mail e senha → Clicar em "Entrar" → Sistema validar credenciais → Sistema gerar token JWT (Access Token + Refresh Token) → Redirecionar para a tela inicial correspondente ao perfil do usuário (catálogo para consumidor, painel para lojista, tela de entregas para entregador).

- **Exceções:** E-mail não cadastrado; senha incorreta; conta desativada; conta pendente de verificação de e-mail; limite de tentativas excedido (rate limiting).

---

### 05. Recuperação de Senha

Abrir tela de login → Selecionar "Esqueci minha senha" → Informar e-mail cadastrado → Sistema enviar código de verificação por e-mail → Usuário informar código no aplicativo → Sistema validar código → Cadastrar nova senha (com confirmação) → Sistema atualizar senha com hash BCrypt → Confirmar alteração → Redirecionar para tela de login.

- **Exceções:** E-mail não cadastrado; código expirado; código inválido; nova senha fora dos critérios mínimos de segurança.

---

### 06. Edição de Perfil

Realizar login no aplicativo → Acessar menu de perfil → Selecionar "Editar Perfil" → Alterar informações desejadas (nome, telefone, foto de perfil, endereço de entrega) → Salvar alterações → Sistema validar dados atualizados → Sistema confirmar atualização com sucesso.

- **Exceções:** Dados inválidos (telefone, CEP); tentativa de alteração de CPF ou e-mail sem revalidação; foto de perfil em formato não suportado.
- **Observação:** Dados sensíveis como CPF e e-mail exigem revalidação via código de verificação.

---

### 07. Cadastro de Produto

Lojista realizar login → Acessar painel da loja → Selecionar "Cadastrar Novo Produto" → Informar nome do produto → Informar descrição detalhada → Selecionar categoria (ex: camisetas, calças, vestidos, acessórios) → Informar tamanhos disponíveis (PP, P, M, G, GG, etc.) → Informar preço → Fazer upload de fotos do produto (mín. 1, máx. 5) → Informar quantidade em estoque → Clicar em "Publicar" → Sistema validar dados e imagens → Produto publicado e visível no catálogo.

- **Exceções:** Campos obrigatórios vazios; preço inválido (zero ou negativo); imagem em formato não suportado; tamanho de arquivo excedido; limite de produtos atingido (plano gratuito, se aplicável).

---

### 08. Edição de Produto

Lojista realizar login → Acessar painel da loja → Selecionar "Meus Produtos" → Selecionar o produto desejado → Clicar em "Editar" → Alterar informações desejadas (nome, descrição, preço, tamanhos, fotos, estoque) → Salvar alterações → Sistema validar dados → Sistema confirmar atualização do produto.

- **Exceções:** Produto com pedido em andamento (alerta ao lojista); preço alterado para valor inválido; tentativa de remover todas as fotos.

---

### 09. Exclusão / Desativação de Produto

Lojista realizar login → Acessar painel da loja → Selecionar "Meus Produtos" → Selecionar o produto desejado → Clicar em "Desativar Produto" → Sistema verificar se há pedidos pendentes vinculados ao produto → Confirmar desativação → Produto removido do catálogo público (soft delete — mantido no banco para histórico).

- **Exceções:** Produto vinculado a pedidos pendentes ou em entrega (bloqueio da exclusão até conclusão).

---

### 10. Busca e Filtragem de Produtos

Consumidor realizar login → Acessar tela de catálogo/home → Digitar termo de busca no campo de pesquisa ou navegar por categorias → Aplicar filtros desejados: categoria, tamanho, faixa de preço, proximidade geográfica (km) → Sistema consultar produtos ativos com base nos filtros e localização do consumidor → Exibir resultados ordenados por relevância/proximidade → Consumidor visualizar cards dos produtos com foto, nome, preço e nome da loja.

- **Exceções:** Nenhum resultado encontrado para os filtros aplicados (exibir sugestão de busca alternativa); erro na obtenção de localização do usuário (solicitar permissão de GPS ou informar CEP manualmente).

---

### 11. Adicionar Produto ao Carrinho

Consumidor navegar pelo catálogo → Selecionar produto desejado → Visualizar página de detalhes (fotos, descrição, tamanhos disponíveis, preço, loja) → Selecionar tamanho desejado → Selecionar quantidade → Clicar em "Adicionar ao Carrinho" → Sistema verificar disponibilidade em estoque → Produto adicionado ao carrinho → Sistema exibir confirmação e atalho para o carrinho.

- **Exceções:** Tamanho esgotado; estoque insuficiente para a quantidade solicitada; produto desativado entre a visualização e a adição.

---

### 12. Finalização de Compra (Checkout)

Consumidor acessar o carrinho → Revisar itens, tamanhos e quantidades → Confirmar ou alterar endereço de entrega → Selecionar forma de pagamento → Sistema calcular valor total (itens + frete, se aplicável) → Consumidor confirmar o pedido → Sistema processar pagamento via gateway (Mercado Pago / Stripe) → Pagamento aprovado → Sistema gerar pedido com status **"PENDENTE"** → Lojista receber notificação do novo pedido → Sistema exibir confirmação de compra com número do pedido ao consumidor.

- **Exceções:** Carrinho vazio; endereço de entrega fora da área de cobertura; pagamento recusado pelo gateway; produto indisponível entre a adição ao carrinho e o checkout (estoque esgotado); erro de comunicação com o gateway de pagamento (tentar novamente ou sugerir outra forma de pagamento).

---

### 13. Recebimento e Confirmação de Pedido

Lojista receber notificação de novo pedido (push + in-app) → Acessar painel de pedidos → Visualizar detalhes do pedido (itens, tamanhos, quantidade, valor, endereço do consumidor) → Verificar disponibilidade em estoque → **Confirmar** ou **Recusar** o pedido → Se confirmado: status atualizado para **"CONFIRMADO"** e consumidor notificado → Se recusado: status atualizado para **"CANCELADO"**, motivo informado, e reembolso automático iniciado.

- **Exceções:** Pedido não respondido dentro do prazo limite (cancelamento automático com reembolso); produto sem estoque no momento da confirmação.

---

### 14. Acompanhamento de Pedido

Consumidor realizar login → Acessar "Meus Pedidos" → Selecionar pedido desejado → Visualizar status atual do pedido (PENDENTE → CONFIRMADO → EM PREPARO → SAIU PARA ENTREGA → ENTREGUE) → Sistema atualizar status em tempo real via notificação.

- **Exceções:** Pedido cancelado pelo lojista (exibir status "CANCELADO" com motivo); atraso na entrega (exibir alerta ao consumidor).

---

### 15. Histórico de Pedidos (Consumidor)

Consumidor realizar login → Acessar menu → Selecionar "Histórico de Pedidos" → Visualizar lista de pedidos realizados com data, loja, itens, valor total e status → Selecionar um pedido para ver detalhes completos → Opção de refazer um pedido anterior (adicionar mesmos itens ao carrinho).

- **Exceções:** Nenhum pedido realizado (exibir mensagem incentivando a primeira compra).

---

### 16. Histórico de Vendas (Lojista)

Lojista realizar login → Acessar painel da loja → Selecionar "Histórico de Vendas" → Visualizar lista de pedidos recebidos com data, consumidor, itens, valor e status → Filtrar por período, status ou produto → Selecionar um pedido para ver detalhes completos.

- **Exceções:** Nenhuma venda realizada (exibir mensagem sugerindo otimização do catálogo).

---

### 24. Configurações do Aplicativo

Realizar login no aplicativo → Acessar menu de configurações → Alterar configurações desejadas (notificações push, preferências de idioma, tema claro/escuro, gerenciar endereços salvos) → Salvar configurações → Sistema confirmar atualização.

- **Exceções:** Erro ao salvar preferências (notificar o usuário e solicitar nova tentativa).

---

### 25. Logout

Usuário acessar menu principal → Selecionar opção "Sair" → Sistema solicitar confirmação ("Deseja realmente sair?") → Usuário confirmar → Sistema invalidar tokens JWT da sessão → Sessão encerrada → Aplicativo retornar à tela de login.

- **Exceções:** Falha na invalidação do token (limpar dados locais e forçar logout).

---

## Fluxos — Pós-MVP

---

### 17. Delivery — Coleta e Entrega

Lojista confirmar pedido e marcar como **"PRONTO PARA COLETA"** → Sistema buscar entregadores disponíveis na região da loja → Entregador receber notificação de nova entrega disponível → Entregador aceitar a entrega → Status atualizado para **"SAIU PARA COLETA"** → Entregador se deslocar até a loja → Entregador confirmar coleta (check-in na loja) → Status atualizado para **"SAIU PARA ENTREGA"** → Entregador se deslocar até o endereço do consumidor → Consumidor receber notificação de que o produto está a caminho → Entregador entregar o produto → Consumidor confirmar recebimento no app → Status atualizado para **"ENTREGUE"**.

- **Exceções:** Nenhum entregador disponível (notificar lojista com estimativa de tempo); entregador cancelar após aceitar (redirecionar para outro entregador); consumidor ausente no endereço (entregador registrar tentativa e reagendar); produto danificado na entrega (registrar ocorrência).

---

### 18. Solicitação de Devolução

Consumidor realizar login → Acessar "Meus Pedidos" → Selecionar pedido com status **"ENTREGUE"** → Verificar se está dentro do prazo de devolução → Clicar em "Solicitar Devolução" → Informar motivo da devolução (tamanho errado, caimento diferente, produto com defeito, outro) → Confirmar solicitação → Sistema criar registro de devolução com status **"SOLICITADA"** → Lojista receber notificação da solicitação → Sistema acionar entregador para coleta de devolução.

- **Exceções:** Prazo de devolução expirado (bloquear solicitação); produto de categoria não-retornável (informar ao consumidor); pedido já com devolução em andamento.

---

### 19. Processamento da Devolução

Sistema acionar entregador disponível para coleta → Entregador aceitar a coleta de devolução → Entregador se deslocar até o endereço do consumidor → Consumidor entregar o produto ao entregador → Entregador confirmar coleta → Entregador se deslocar até a loja → Entregador entregar o produto devolvido ao lojista → Lojista inspecionar o produto → Lojista **confirmar** ou **recusar** a devolução no app → Se confirmada: status atualizado para **"DEVOLVIDO"** e reembolso processado automaticamente via gateway → Se recusada: lojista informar motivo, consumidor notificado, e produto reenviado ao consumidor.

- **Exceções:** Produto devolvido em más condições (lojista recusar devolução com evidência fotográfica); entregador não localizar o consumidor (reagendar coleta); disputa entre consumidor e lojista (escalar para o administrador).

---

### 20. Avaliação de Produto / Loja

Consumidor realizar login → Acessar "Meus Pedidos" → Selecionar pedido com status **"ENTREGUE"** → Clicar em "Avaliar" → Atribuir nota (1 a 5 estrelas) ao produto → Escrever comentário (opcional) → Atribuir nota à loja (opcional) → Confirmar avaliação → Sistema publicar avaliação vinculada ao produto e à loja → Lojista receber notificação da nova avaliação.

- **Exceções:** Consumidor tentar avaliar sem ter recebido o produto; avaliação com conteúdo ofensivo (filtro automatizado + moderação); tentativa de avaliação duplicada para o mesmo pedido.

---

### 21. Chat entre Consumidor e Lojista

Consumidor acessar página de um produto ou pedido → Clicar em "Conversar com a Loja" → Sistema abrir janela de chat via WebSocket → Consumidor enviar mensagem de texto → Lojista receber notificação de nova mensagem → Lojista acessar painel de mensagens → Lojista responder → Conversa em tempo real entre ambos → Qualquer parte pode encerrar a conversa.

- **Exceções:** Lojista offline (mensagem armazenada e entregue quando retornar); envio de conteúdo proibido (filtro automatizado); tentativa de envio de dados sensíveis (alerta ao usuário).

---

### 22. Gestão da Loja (Painel do Lojista)

Lojista realizar login → Acessar "Minha Loja" → Visualizar dashboard com resumo (vendas do dia, pedidos pendentes, produtos ativos, avaliação média) → Gerenciar produtos (cadastrar, editar, desativar) → Gerenciar pedidos (confirmar, recusar, acompanhar status) → Atualizar dados da loja (descrição, logo, horário de funcionamento, dados bancários) → Visualizar relatórios de vendas por período.

- **Exceções:** Loja desativada pelo administrador (exibir aviso e bloquear operações); dados bancários inválidos (bloquear recebimentos até correção).

---

### 23. Painel Administrativo

Administrador realizar login com credenciais de admin → Acessar painel administrativo → Visualizar dashboard geral (total de usuários, lojas ativas, pedidos do dia, volume financeiro) → Gerenciar usuários (ativar, desativar, suspender contas de consumidores, lojistas e entregadores) → Aprovar ou recusar cadastros de novas lojas e entregadores → Gerenciar disputas de devolução escaladas → Visualizar relatórios consolidados → Configurar parâmetros da plataforma (taxa de comissão, prazo de devolução, raio de busca padrão).

- **Exceções:** Tentativa de acesso sem permissão de admin (bloquear e registrar log); operação crítica (exigir confirmação dupla).

---

## Fluxo Principal Completo (Happy Path)

Para referência do ciclo de vida completo de um pedido:

**Consumidor se cadastra** → Busca produtos no catálogo → Filtra por categoria, tamanho, preço e proximidade → Seleciona produto e tamanho → Adiciona ao carrinho → Acessa o carrinho e revisa itens → Confirma endereço de entrega → Realiza pagamento → **Pedido criado (PENDENTE)** → Lojista recebe notificação → Lojista confirma o pedido **(CONFIRMADO)** → Lojista prepara o produto **(PRONTO PARA COLETA)** → Entregador é acionado e aceita → Entregador coleta na loja **(SAIU PARA ENTREGA)** → Entregador entrega ao consumidor → Consumidor confirma recebimento **(ENTREGUE)** → Consumidor pode avaliar produto e loja.

**Em caso de devolução:** Consumidor solicita devolução dentro do prazo → Entregador coleta o produto no endereço do consumidor → Entregador devolve à loja → Lojista confirma recebimento em boas condições → Reembolso processado automaticamente **(DEVOLVIDO/REEMBOLSADO)**.

---

## Legenda

| Símbolo / Termo      | Significado                                                   |
|-----------------------|---------------------------------------------------------------|
| →                     | Próximo passo do fluxo                                        |
| **Exceções**          | Situações de erro ou caminhos alternativos ao fluxo principal |
| **MVP**               | Funcionalidade presente no Mínimo Produto Viável              |
| **Pós-MVP**           | Funcionalidade prevista para a versão completa da plataforma  |
| Status em **NEGRITO** | Estados do ciclo de vida do pedido no sistema                 |

