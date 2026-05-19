## Legendas e Convenções
**RF-W** = Requisito Funcional Web
**RF-M** = Requisito Funcional Mobile
**RNF-W** = Requisito Não Funcional Web
**RNF-M** = Requisito Não Funcional Mobile
**RN-W** = Regra de Negócio Web
**RN-M** = Regra de Negócio Mobile

**Coluna Relação**: indica o vínculo bidirecional entre requisitos e regras de negócio. Em requisitos, aponta as regras que os fundamentam. Em regras, aponta os requisitos que as implementam.

> Arquitetura de plataformas: a Web serve tanto o consumidor (catálogo, compras, acompanhamento) quanto o portal exclusivo do lojista (gestão de produtos, pedidos e financeiro). Lojistas não têm interface mobile, toda gestão é feita via portal web. O app mobile serve o consumidor e o entregador.

---

# 1. Requisitos Web

## 1.1 Requisitos Funcionais
Requisitos funcionais da plataforma web: área pública/consumidor, portal exclusivo do lojista e painel administrativo.

| **Código** | **Descrição** | **Relação** |
| ---------- | ------------- | ----------- |
| **RF-W01** | O sistema deve exibir página inicial com: Boas-vindas, categorias de moda em destaque, vitrine de lojas próximas (baseada em CEP digitado ou geolocalização via browser) e chamada para cadastro/download do app. | **—** |
| **RF-W02** | O sistema deve exibir banner de consentimento de cookies. | **RN-W26** |
| **RF-W03** | O sistema deve permitir o cadastro de consumidor na web com os campos: nome completo, CPF, RG, e-mail, senha, CEP e endereço de entrega principal. Validação inline em tempo real. | **RN-W01, RN-W02, RN-W03** |
| **RF-W04** | O sistema deve permitir login de consumidor com e-mail e senha, com feedback visual de carregamento. | **RN-W03, RN-W04** |
| **RF-W05** | O sistema deve oferecer fluxo de recuperação de senha via e-mail. | **—** |
| **RF-W06** | O sistema deve exibir catálogo de produtos com paginação, vitrine de lojas próximas (raio padrão: 10 km), seções de categorias e banners de promoção (Validar lojas fechadas). | **RN-W07, RN-W08, RN-W09, RN-W10** |
| **RF-W07** | O sistema deve oferecer busca de produtos com autocomplete (sugestões em tempo real por nome de produto, loja e categoria) e filtros combinados: categoria, tamanho, faixa de preço, distância em km e ordenação (relevância, menor preço, maior preço, mais vendidos, novidades). | **RN-W08, RN-W09, RN-W10** |
| **RF-W08** | O sistema deve exibir página de detalhe do produto com: galeria de fotos, nome, descrição completa, tamanhos disponíveis (esgotados visualmente indicados), preço (com preço original riscado se em promoção), estoque por tamanho, nome e avaliação média da loja e botão de adicionar ao carrinho. | **RN-W11, RN-W12, RN-W13** |
| **RF-W09** | O sistema deve exibir página de perfil da loja com: logo, banner, nome, categoria(s), descrição, distância, avaliação média, horário de funcionamento, status (ABERTA/FECHADA) e listagem de produtos ativos paginados. | **RN-W07, RN-W09, RN-W10** |
| **RF-W10** | O sistema deve permitir ao consumidor adicionar produto ao carrinho com seleção obrigatória de tamanho e quantidade. Produto INDISPONÍVEL ou INATIVO não pode ser adicionado; tamanhos esgotados ficam desabilitados. | **RN-W08, RN-W11** |
| **RF-W11** | O sistema deve exibir carrinho com itens agrupados por loja (logo, nome da loja, itens com foto miniatura/nome/tamanho/quantidade/preço), subtotal por loja, frete estimado por loja, total geral e botão de finalizar compra. Itens que ficaram indisponíveis desde a adição devem ser sinalizados. | **RN-W08, RN-W14** |
| **RF-W12** | O sistema deve exibir tela de checkout com: seleção ou adição de endereço de entrega (validando raio de entrega de cada loja do carrinho), estimativa de tempo de entrega por loja, forma de pagamento e resumo final do pedido com total. | **RN-W14, RN-W19** |
| **RF-W13** | O sistema deve processar pagamento via gateway integrado com suporte a cartão de crédito (parcelamento configurável), cartão de débito e PIX (QR Code + copia-e-cola). | **RN-W19, RN-W20** |
| **RF-W14** | O sistema deve exibir tela de confirmação de pedido após pagamento bem-sucedido, com: número de protocolo, resumo de itens por loja, valor pago e instrução de acompanhamento. | **RN-W14, RN-W15** |
| **RF-W15** | O sistema deve exibir timeline visual de acompanhamento de pedido com status: PENDENTE → CONFIRMADO → PRONTO PARA COLETA → EM ENTREGA → ENTREGUE, com horário de cada transição e descrição amigável de cada etapa. | **RN-W15, RN-W16, RN-W28** |
| **RF-W16** | O sistema deve exibir histórico de pedidos do consumidor com listagem ordenada por data, exibindo status, itens resumidos e valor total. Com acesso ao detalhe completo de cada pedido. | **RN-W15, RN-W28** |
| **RF-W17** | O sistema deve permitir ao consumidor gerenciar seu perfil: nome, telefone, foto, e-mail (com confirmação), senha e endereços (adicionar, editar, excluir, definir padrão). | **RN-W03, RN-W25** |
| **RF-W18** | O sistema deve permitir o cadastro de lojista com os campos: nome completo, CPF, CNPJ, e-mail, senha, nome da loja, endereço da loja (com CEP), dados bancários (banco, agência, conta, tipo) e aceite dos Termos de Uso. Validação inline em tempo real. | **RN-W01, RN-W02, RN-W03, RN-W05, RN-W23** |
| **RF-W19** | O sistema deve exibir wizard de configuração inicial da loja (First Run) após o primeiro login do lojista, guiando pelas etapas: (1) dados da loja, (2) logo e banner, (3) categoria(s) e raio de entrega, (4) horário de funcionamento, (5) dados bancários, (6) primeiro produto. O wizard pode ser pulado e retomado. | **RN-W05, RN-W06** |
| **RF-W20** | O sistema deve exibir indicador visual de completude do perfil da loja (barra de progresso percentual) com etapas pendentes listadas no painel, incentivando o lojista a completar o cadastro. | **—** |
| **RF-W21** | O sistema deve permitir ao lojista configurar o status da loja manualmente: ABERTA, FECHADA ou em PAUSA TEMPORÁRIA. Modo pausa suspende novos pedidos sem desativar a conta. Fora do horário configurado, a loja entra em modo FECHADA automaticamente. | **RN-W06, RN-W07** |
| **RF-W22** | O sistema deve permitir ao lojista configurar horários de funcionamento por dia da semana (horário de abertura e fechamento para cada dia, com possibilidade de marcar dia como fechado). Exibido no perfil público da loja no app e na web. | **RN-W06, RN-W07** |
| **RF-W23** | O sistema deve permitir ao lojista cadastrar produto com campos obrigatórios: nome, descrição, categoria, ao menos 1 foto, tamanhos disponíveis com estoque individual por tamanho, preço de venda. Campos opcionais: preço promocional (com data início/fim), tags (ex.: 'inverno 2026', 'plus size'). | **RN-W11, RN-W12, RN-W13** |
| **RF-W24** | O sistema deve exibir preço promocional ativo com o preço original riscado e percentual de desconto calculado automaticamente. Ao expirar a data de término, o produto volta ao preço original sem ação manual. | **RN-W13, RN-W22** |
| **RF-W25** | O sistema deve exibir galeria de fotos por produto com: upload múltiplo (arrastando ou selecionando), reordenação por arrastar e soltar, definição de foto de capa e visualização prévia antes de salvar. | **RN-W12** |
| **RF-W26** | O sistema deve permitir ao lojista editar qualquer campo de produto cadastrado. | **RN-W11** |
| **RF-W27** | O sistema deve permitir ao lojista ativar e desativar produtos individualmente (toggle) ou em lote (seleção múltipla + ação em massa). Produto desativado some imediatamente do catálogo público sem excluir dados. | **RN-W11** |
| **RF-W28** | O sistema deve permitir ao lojista excluir permanentemente produto que nunca teve pedido associado. Produto com histórico de pedidos só pode ser desativado, preservando integridade do histórico transacional. **(MUITO IMPORTANTE)** | **RN-W11** |
| **RF-W29** | O sistema deve permitir ao lojista atualizar estoque por tamanho diretamente na listagem (campo de edição inline por tamanho) e na tela de detalhe do produto, com histórico de alterações de estoque. | **RN-W11** |
| **RF-W30** | O sistema deve exibir alerta de estoque baixo no painel quando a soma do estoque de todos os tamanhos de um produto atingir limiar configurável pelo lojista (padrão: 3 unidades), com destaque visual na listagem de produtos. | **RN-W11** |
| **RF-W31** | O sistema deve exibir dashboard de pedidos em tempo real organizado em colunas Kanban por status: Novos Pedidos / Confirmados / Prontos para Coleta / Em Entrega / Concluídos. Atualização sem recarregar página via WebSocket. Alerta sonoro e badge visual para novos pedidos. | **RN-W16, RN-W17** |
| **RF-W32** | O sistema deve exibir tela de detalhe do pedido para o lojista com: número de protocolo, foto miniatura e detalhes de cada item (nome, tamanho, quantidade, preço), endereço de entrega (bairro e cidade, sem número completo), forma de pagamento e histórico de status do pedido. | **RN-W16** |
| **RF-W33** | O sistema deve permitir ao lojista confirmar pedido dentro do prazo de 30 minutos. Confirmação avança o status, notifica o consumidor no app/web e inicia a busca por entregador. | **RN-W16, RN-W17** |
| **RF-W34** | O sistema deve permitir ao lojista recusar pedido com seleção obrigatória de motivo (produto esgotado, loja fechada temporariamente, endereço fora do raio, outro). A recusa cancela o pedido, estorna o pagamento e notifica o consumidor. | **RN-W16, RN-W17, RN-W20** |
| **RF-W35** | O sistema deve permitir ao lojista marcar pedido como PRONTO PARA COLETA, sinalizando que o produto está embalado e aguardando o entregador. Ao marcar, os entregadores disponíveis na região são notificados. | **RN-W16** |
| **RF-W36** | O sistema deve exibir histórico completo de pedidos do lojista com filtros: período, status, valor mínimo/máximo e busca por protocolo ou nome do produto. | **—** |
| **RF-W37** | O sistema deve exibir dashboard financeiro do lojista com: total de vendas brutas, total de comissões da plataforma, valor líquido a receber, ticket médio e comparativo com período anterior. | **RN-W21** |
| **RF-W38** | O sistema deve permitir ao lojista editar as informações públicas da loja: nome, descrição, logo, banner, categoria(s), endereço, raio máximo de entrega e tempo médio de preparação de pedidos. | **—** |
| **RF-W39** | O sistema deve permitir ao lojista atualizar dados bancários com reautenticação (senha atual) obrigatória. Alteração gera entrada em log de auditoria e e-mail de confirmação ao lojista. | **RN-W25** |
| | **Daqui para baixo é discutível, ela entra se caso formos ter algum painel administrador (só a gente tem acesso)** | |
| **RF-W40** | O sistema deve exibir ao administrador painel de aprovação de novos cadastros de lojistas com: dados enviados, documentos (CNPJ, dados bancários mascarados) e ações de aprovar, reprovar (com motivo) ou solicitar complemento. | **—** |
| **RF-W41** | O sistema deve permitir ao administrador ativar, suspender e excluir contas de lojistas, consumidores e entregadores, com campo de motivo e registro em log de auditoria. | **—** |
| **RF-W42** | O sistema deve permitir ao administrador configurar a taxa de comissão por lojista ou por faixa de plano, com data de vigência, histórico de alterações e cálculo automático do impacto nos repasses futuros. | **RN-W21** |

---

## 1.2 Requisitos Não Funcionais
Requisitos não funcionais da plataforma web.

| **Código**  | **Descrição**                                                                               | **Relação** |
| ----------- | ------------------------------------------------------------------------------------------- | ----------- |
| **RNF-01**  | O sistema deve ter tempo de resposta inferior a 2 segundos para 95% das requisições         | **—**       |
| **RNF-W02** | O sistema deve ser responsivo, adaptando-se a desktop, tablet e mobile                      | **—**       |
| **RNF-W03** | O sistema deve garantir disponibilidade de 99,5% mensal.                                    | **—**       |
| **RNF-W04** | O sistema deve seguir padrões de acessibilidade (WCAG 2.1 nível AA)                         | **—**       |
| **RNF-W05** | Todas as comunicações devem ser feitas via HTTPS (TLS 1.2+).                                | **RN-W25**  |
| **RNF-W06** | O sistema deve ser compatível com os principais navegadores (Chrome, Firefox, Edge, Safari) | **—**       |
| **RNF-W07** | Logs de auditoria devem ser armazenados por no mínimo 6 meses                               | **RN-W25**  |

---

# 2. Requisitos Mobile

## 2.1 Requisitos Funcionais
Requisitos funcionais do aplicativo mobile: consumidor (onboarding, catálogo, busca, compra, pedido, perfil) e entregador (disponibilidade, entregas, rastreamento, ganhos).

| **Código** | **Descrição** | **Relação** |
| ---------- | ------------- | ----------- |
| **RF-M01** | O aplicativo deve exibir tela de splash com identidade visual da plataforma ao ser aberto (máx. 2 s), redirecionando para login ou tela principal. | **—** |
| **RF-M02** | O aplicativo deve exibir tela de consentimento LGPD no primeiro acesso, antes de qualquer coleta de dado pessoal. Sem aceite explícito do botão de confirmação, o app permanece bloqueado. | **RN-M03** |
| **RF-M03** | O aplicativo deve exibir fluxo de onboarding com 4 telas: (1) descubra lojas locais perto de você, (2) busque por categoria, tamanho e preço, (3) pague no app e receba em casa, (4) não gostou? Faz o L. Com indicador de progresso e botão de pular. | **—** |
| **RF-M04** | O aplicativo deve permitir cadastro de consumidor com: nome completo, CPF, RG, e-mail, senha, CEP e endereço de entrega principal. Validação inline em tempo real. | **RN-M01, RN-M02** |
| **RF-M05** | O aplicativo deve permitir login do consumidor com e-mail e senha, com feedback de carregamento. | **RN-M05** |
| **RF-M06** | O aplicativo deve oferecer recuperação de senha via e-mail. | **—** |
| **RF-M07** | O aplicativo deve permitir logout com confirmação. Dados do carrinho local são preservados para reutilização no próximo login. | **—** |
| **RF-M08** | O aplicativo deve oferecer tela de login para entregador previamente cadastrado no portal administrativo, com e-mail e senha. Ao autenticar como DELIVERER, o app exibe a interface do entregador em vez da do consumidor. | **—** |
| **RF-M09** | O aplicativo deve exibir tela principal do consumidor com: banner rotativo de destaque (promoções e lojas parceiras), grade de categorias (feminino, masculino, infantil, calçados, acessórios, íntimos, fitness, etc.), seção 'Lojas Abertas Agora' ordenadas por proximidade, seção 'Mais Vendidos' e seção 'Novidades da Semana'. | **RN-M06, RN-M07** |
| **RF-M10** | O aplicativo deve exibir somente lojas com status ABERTA e dentro do raio de entrega do endereço padrão do consumidor nas seções de destaque da home. | **RN-M06, RN-M07** |
| **RF-M11** | O aplicativo deve exibir tela de todas as categorias disponíveis com ícones ilustrativos e contador de produtos ativos por categoria. | **—** |
| **RF-M12** | O aplicativo deve oferecer campo de busca global persistente no topo da tela com autocomplete em tempo real para: nome de produto, nome de loja e categoria. | **RN-M07** |
| **RF-M13** | O aplicativo deve exibir tela de resultados de busca com filtros combinados: categoria, tamanho (PP, P, M, G, GG, XGG, 34–56 ou numeração de calçado), faixa de preço (slider), distância máxima (1–50 km) e ordenação. | **RN-M06, RN-M07, RN-M09** |
| **RF-M14** | O aplicativo deve exibir tela de detalhe do produto com: galeria de fotos deslizável, nome, descrição, tamanhos disponíveis (esgotados visivelmente desabilitados), preço (com original riscado se em promoção e tag 'X% OFF'), estoque por tamanho selecionado (alerta 'Apenas N restantes' quando ≤ 5), nome e avaliação da loja e botão de adicionar ao carrinho. | **RN-M08, RN-M10, RN-M11, RN-M12** |
| **RF-M15** | O aplicativo deve exibir tela de perfil da loja com: logo, banner, nome, categoria(s), descrição, distância, avaliação média (número de estrelas e quantidade de avaliações), horário de funcionamento com indicação ABERTA/FECHADA em tempo real e listagem de produtos ativos paginados. | **RN-M06, RN-M07** |
| **RF-M16** | O aplicativo deve exibir badge 'Novo' em produtos cadastrados há menos de 7 dias e badge 'Promoção' com percentual de desconto em produtos com preço promocional ativo. | **—** |
| **RF-M17** | O aplicativo deve exibir tela de carrinho com itens agrupados por loja: logo e nome da loja, cada item com foto miniatura, nome, tamanho selecionado, controles de quantidade (+/−, mínimo 1), preço unitário e subtotal. Subtotal por loja, frete estimado por loja e total geral ao final. | **RN-M13, RN-M14, RN-M16, RN-M17** |
| **RF-M18** | O aplicativo deve permitir remover itens do carrinho por swipe para a esquerda ou botão de lixeira, com confirmação via toast e ação 'Desfazer' disponível por 5 segundos. | **RN-M13** |
| **RF-M19** | O aplicativo deve verificar disponibilidade de todos os itens do carrinho ao abrir a tela do carrinho e antes de avançar para o checkout. Itens que ficaram INDISPONÍVEIS desde a adição são sinalizados com banner de aviso e opção de removê-los. | **RN-M14** |
| **RF-M20** | O aplicativo deve exibir contador de itens no carrinho no ícone de carrinho da barra de navegação, atualizado em tempo real a cada adição ou remoção. | **—** |
| **RF-M21** | O aplicativo deve permitir ao consumidor gerenciar endereços de entrega diretamente no checkout: adicionar novo endereço com validação de CEP, editar e definir como padrão. Endereços fora do raio de entrega de alguma loja do carrinho são sinalizados com aviso. | **RN-M15, RN-M16, RN-M17** |
| **RF-M22** | O aplicativo deve exibir aviso ao consumidor quando alguma loja do carrinho não realiza entrega no endereço selecionado, com opção de: remover os itens da loja em questão ou selecionar outro endereço. | **RN-M15** |
| **RF-M23** | O aplicativo deve exibir tela de seleção de forma de pagamento com as opções: cartão de crédito (salvar cartão para uso futuro, seleção de parcelas), cartão de débito e PIX. | **RN-M18** |
| **RF-M24** | O aplicativo deve exibir tela de revisão de pagamento antes da confirmação final, com: forma de pagamento, número de parcelas (se crédito), valor total e botão de confirmar pedido com ícone de cadeado. | **RN-M18** |
| **RF-M25** | O aplicativo deve processar pagamento via gateway integrado com suporte a cartão de crédito (até X parcelas), cartão de débito e PIX (QR Code para escanear + botão de copiar código). Ambiente de homologação no MVP. | **RN-M18, RN-M19** |
| **RF-M26** | O aplicativo deve exibir tela de confirmação de pedido após pagamento bem-sucedido com: animação de sucesso, número de protocolo, resumo dos itens por loja e instrução de acompanhamento com deep link para a tela do pedido. | **—** |
| **RF-M27** | O aplicativo deve tratar falhas de pagamento exibindo mensagem amigável com o motivo específico (cartão recusado, saldo insuficiente, tempo de PIX expirado, erro de rede) e opção de tentar novamente com a mesma forma ou escolher outra. | **RN-M19** |
| **RF-M28** | O aplicativo deve exibir tela de acompanhamento de pedido com timeline visual e descritiva: PENDENTE (aguardando confirmação do lojista, contador regressivo de 30 min visível) → CONFIRMADO → PRONTO PARA COLETA → EM ENTREGA → ENTREGUE. Cada etapa com horário de transição e mensagem contextual amigável. | **RN-M17, RN-M20, RN-M21** |
| **RF-M29** | O aplicativo deve enviar notificação push e exibir notificação in-app ao consumidor em cada mudança de status do pedido com mensagens contextuais (ex.: 'Sua blusa já está com o entregador! Chegando em ~20 minutos.'). | **RN-M22, RN-M23** |
| **RF-M30** | O aplicativo deve exibir tela de detalhe do pedido com: número de protocolo, itens (foto, nome, tamanho, quantidade, preço unitário), loja(s), endereço de entrega, timeline de status com horários, forma de pagamento, frete e valor total. | **—** |
| **RF-M31** | O aplicativo deve exibir tela de perfil do consumidor com: foto de perfil, nome, e-mail, CPF mascarado, telefone, botões de acesso rápido a endereços, histórico de pedidos, favoritos e configurações. | **—** |
| **RF-M32** | O aplicativo deve permitir edição de dados pessoais: nome, telefone e foto de perfil. Alteração de e-mail exige confirmação via link enviado ao novo endereço. Alteração de senha exige senha atual. | **RN-M02** |
| **RF-M33** | O aplicativo deve exibir tela de configurações do app com: opção de tema (claro/escuro) com persistência, gerenciamento de permissões do sistema (localização, câmera, notificações) com status atual e atalho para configurações do SO. | **RN-M26** |
| **RF-M34** | O aplicativo deve disponibilizar solicitação de exclusão de conta e dados conforme LGPD, com confirmação em duas etapas (botão + modal de confirmação com digitação de 'CONFIRMAR') e e-mail de confirmação. Dados excluídos em até 15 dias úteis. | **RN-M27** |
| **RF-M35** | O aplicativo deve exibir ao entregador tela principal com: status atual (ONLINE/OFFLINE) em destaque, toggle de disponibilidade, contador de entregas concluídas no dia, ganhos do dia e mapa da região atual. | **RN-M28** |
| **RF-M36** | O aplicativo deve notificar o entregador via push e alerta na tela principal quando uma nova entrega disponível surgir na sua região, com detalhes: nome e endereço da loja (bairro), bairro do consumidor, distância estimada total e valor estimado da entrega. O entregador tem 60 segundos para aceitar; após o timeout, a entrega é ofertada ao próximo. | **RN-M29, RN-M30** |
| **RF-M37** | O aplicativo deve exibir ao entregador tela de detalhe da entrega após aceitar, com: endereço completo da loja, nome e endereço do consumidor (sem número de telefone completo), rota integrada no mapa com opção de abrir no app de navegação do dispositivo e botão de confirmar coleta. | **RN-M31, RN-M32** |
| **RF-M38** | O aplicativo deve exibir ao entregador tela para relatar problema durante a entrega com: tipo de problema (consumidor ausente, endereço não encontrado, produto danificado, acidente/imprevisto pessoal), descrição opcional e opção de contato com suporte via chat. | **—** |
| **RF-M39** | O aplicativo deve exibir ao entregador histórico de entregas com: data, tipo (entrega/coleta devolução), endereços, status e valor recebido por entrega. Totalizadores de ganhos: dia, semana e mês. | **—** |
| **RF-M40** | O aplicativo deve exibir ao entregador tela de perfil com: foto, nome, dados do veículo (tipo e placa) e status de cadastro. Com opção de solicitar atualização de dados ao admin. | **—** |

---

## 2.2 Requisitos Não Funcionais
Requisitos não funcionais da plataforma mobile.

| Código  | Descrição                                                                                    | Relação |
| ------- | -------------------------------------------------------------------------------------------- | ------- |
| RNF-M01 | O app deve iniciar em até 2 segundos em dispositivos médios.                                 | RF-M01  |
| RNF-M02 | O app deve funcionar em Android 8+ e iOS 13+.                                                | —       |
| RNF-M03 | O app deve consumir no máximo 150MB de armazenamento.                                        | —       |
| RNF-M04 | O app deve seguir boas práticas de UX mobile (Material Design / Human Interface Guidelines). | —       |
| RNF-M05 | O app deve proteger dados sensíveis com criptografia local segura                            | RN-M18  |
| RNF-M06 | O app deve ter taxa de crash inferior a 1%.                                                  | —       |
| RNF-M07 | O app deve suportar diferentes tamanhos de tela e densidades.                                | —       |

---

# 3. Regras de Negócio Web
Regras de negócio da plataforma web: cadastro e autenticação, status de loja, busca e catálogo, ciclo de vida do pedido, pagamento e financeiro, avaliação, segurança e LGPD, notificações.

| **Código** | **Descrição** | **Relação** |
| ---------- | ------------- | ----------- |
| **RN-W01** | O e-mail é identificador único no sistema, nenhum e-mail pode estar vinculado a mais de uma conta, independentemente do tipo (CONSUMER, STORE, DELIVERER, ADMIN). | **RF-W03, RF-W04, RF-W18** |
| **RN-W02** | O CPF é único no sistema, diferentes tipos de conta não podem compartilhar o mesmo CPF. Validação dos dígitos verificadores obrigatória antes de persistir. Mensagem de erro não revela o vínculo existente. | **RF-W03, RF-W18** |
| **RN-W03** | Senha deve ter no mínimo 6 caracteres com ao menos 1 número e 1 letra maiúscula. | **RF-W03, RF-W04, RF-W05, RF-W17, RF-W18** |
| **RN-W04** | Proteção contra força bruta no login: após 5 tentativas falhas consecutivas para o mesmo e-mail, a conta é bloqueada temporariamente por 15 minutos com countdown informado ao usuário. Controle gerenciado via Redis para consistência entre instâncias. IP com mais de 20 tentativas em 5 minutos é bloqueado independentemente da conta. | **RF-W04** |
| **RN-W05** | Lojista recém-cadastrado inicia com status PENDENTE_APROVACAO. Enquanto pendente, pode configurar a loja e produtos, mas a loja não aparece publicamente. O status muda para ATIVA após aprovação administrativa ou automaticamente após validação básica dos dados. | **RF-W18, RF-W19** |
| **RN-W06** | A loja pode ter os seguintes status: PENDENTE_APROVACAO → ATIVA → PAUSADA / FECHADA (automático por horário) / SUSPENSA (por admin) / INATIVA (desativada pelo lojista). Loja PAUSADA suspende novos pedidos mas mantém o perfil público visível com indicação de pausa. Loja SUSPENSA ou INATIVA não aparece em nenhuma busca ou resultado público. | **RF-W21, RF-W22** |
| **RN-W07** | O sistema fecha a loja automaticamente (status FECHADA) fora do horário de funcionamento configurado pelo lojista. A loja reabre automaticamente no horário de abertura configurado. O lojista pode sobrepor o status manualmente a qualquer momento (abrir antecipadamente ou fechar antes do horário). | **RF-W21, RF-W22** |
| **RN-W08** | Loja FECHADA ainda aparece nos resultados de busca e no mapa com indicação de status e previsão de próxima abertura. Consumidor pode visualizar o catálogo e favoritar produtos, mas não pode adicionar itens ao carrinho de uma loja fechada. | **RF-W06, RF-W07, RF-W09, RF-W10, RF-W11** |
| **RN-W09** | Busca por proximidade usa coordenadas geográficas (latitude/longitude) obtidas por geocodificação do CEP do consumidor ou geolocalização do browser. Raio padrão: 10 km, ajustável de 1 km a 50 km. Lojas e produtos fora do raio não aparecem nos resultados. | **RF-W06, RF-W07, RF-W09** |
| **RN-W10** | Os resultados de busca retornam apenas produtos ATIVOS de lojas ATIVAS ou FECHADAS. Produtos INATIVOS e produtos de lojas SUSPENSAS/INATIVAS são completamente ocultados dos resultados públicos. | **RF-W07, RF-W08, RF-W09** |
| **RN-W11** | Produto deve ter obrigatoriamente: nome, descrição, categoria, ao menos 1 foto, ao menos 1 tamanho com estoque ≥ 0, preço de venda > R$ 0,01. Produto com estoque total = 0 (soma de todos os tamanhos) é marcado INDISPONIVEL e exibido no catálogo com essa indicação, não é excluído. Produto INATIVO não aparece no catálogo público. | **RF-W08, RF-W10, RF-W23, RF-W26, RF-W27, RF-W28, RF-W29, RF-W30** |
| **RN-W12** | Fotos de produto: máximo 5 MB por imagem; até 8 fotos por produto. Formatos aceitos: JPG, PNG e WebP. O servidor valida tipo MIME, não apenas a extensão. Imagens são redimensionadas e otimizadas no upload, gerando versões thumb (200×200) e full (800×800). | **RF-W23, RF-W25** |
| **RN-W13** | Preço de venda deve ser positivo (mín. R$ 0,01, máx. R$ 99.999,99) com no máximo 2 casas decimais. Preço promocional deve ser menor que o preço de venda e menor que 90% de desconto. Ao expirar a data de término da promoção, o produto retorna ao preço original automaticamente via job agendado. | **RF-W23, RF-W24** |
| **RN-W14** | Pedido com itens de mais de uma loja é automaticamente dividido em sub-pedidos (order splitting), um por loja. Cada sub-pedido possui seu próprio ciclo de vida, entregador e pagamento de frete. O consumidor paga e visualiza o resumo consolidado, mas cada sub-pedido é gerenciado independentemente pelo lojista. | **RF-W11, RF-W12, RF-W14, RF-W15, RF-W16** |
| **RN-W15** | O ciclo de vida do pedido segue a sequência: PENDENTE → CONFIRMADO → PRONTO_PARA_COLETA → EM_ENTREGA → ENTREGUE. Fluxos alternativos: PENDENTE/CONFIRMADO → CANCELADO (com motivo). Transições fora da sequência esperada retornam HTTP 422. Cada transição registra timestamp e usuário responsável. | **RF-W14, RF-W15, RF-W16, RF-W33, RF-W34, RF-W35** |
| **RN-W16** | Ao receber um novo pedido, o lojista tem exatamente 30 minutos para confirmar ou recusar. Após o timeout, o pedido é CANCELADO automaticamente via job agendado: o pagamento é estornado integralmente e o consumidor é notificado. O lojista recebe alerta de pedido expirado. | **RF-W31, RF-W32, RF-W33, RF-W34, RF-W35** |
| **RN-W17** | O lojista pode recusar pedido apenas enquanto o status for PENDENTE. A recusa exige seleção de motivo obrigatório. Pedidos CONFIRMADOS só podem ser cancelados pelo administrador da plataforma. O cancelamento de qualquer pedido aciona o estorno integral ao consumidor via gateway. | **RF-W34** |
| **RN-W18** | O lojista só pode acessar, modificar e gerenciar seus próprios recursos (produtos, pedidos, dados financeiros). Qualquer tentativa de acessar recurso de outra loja retorna HTTP 403 Forbidden. | **RF-W23, RF-W26, RF-W27, RF-W28, RF-W29, RF-W31, RF-W32, RF-W33, RF-W34, RF-W35, RF-W36, RF-W37** |
| **RN-W19** | O pagamento é pré-autorizado (reservado) no gateway no momento em que o consumidor confirma o pedido. A captura definitiva ocorre quando o lojista confirma. Em recusa, timeout ou cancelamento pelo consumidor antes da confirmação, a pré-autorização é liberada sem custo. Após captura, estorno segue as regras do gateway (PIX: imediato; cartão: até 5 dias úteis). | **RF-W12, RF-W13, RF-W14** |
| **RN-W20** | O reembolso é disparado automaticamente via gateway nos eventos: (a) timeout do lojista, (b) recusa do lojista, (c) cancelamento pelo consumidor antes da confirmação, (d) intervenção do admin em disputa. O gateway retorna o comprovante de estorno que deve ser registrado e exibido ao consumidor. | **RF-W13, RF-W34** |
| **RN-W21** | A comissão da plataforma é calculada sobre o valor dos produtos (valor do frete não entra na base de cálculo). Percentual configurável por contrato do lojista (default configurado pelo admin). O repasse ao lojista ocorre em D+2 após o status ENTREGUE ser confirmado. Devoluções e cancelamentos após captura deduzem a comissão provisionada do próximo repasse. | **RF-W37, RF-W42** |
| **RN-W22** | Preço promocional é válido apenas no intervalo entre a data de início e a data de término configuradas pelo lojista. Fora deste intervalo, o produto exibe apenas o preço normal. O sistema verifica e aplica ou remove a promoção via job agendado a cada hora. | **RF-W24** |
| **RN-W23** | O CNPJ do lojista deve ter seus dígitos verificadores validados no cadastro. Integrar com API da Receita Federal para verificar se o CNPJ está ativo. Lojista com CNPJ inapto/cancelado não deve ter cadastro aprovado. | **RF-W18** |
| **RN-W24** | Avaliação de produto/loja só pode ser submetida pelo consumidor que realizou a compra (verificação por order_id + user_id), com status ENTREGUE confirmado e dentro de 7 dias após a entrega. Um consumidor pode avaliar o mesmo produto/loja no máximo uma vez por pedido. | **—** |
| **RN-W25** | Dados sensíveis (CPF, RG, CNPJ, dados bancários completos) devem ser criptografados em repouso (AES-256 ou equivalente). Nas respostas da API, CPF é mascarado (***.456.789-**), CNPJ é mascarado (**.123.456/0001-**), dados bancários exibem apenas banco e últimos 4 dígitos da conta. Alteração de dados bancários exige reautenticação e gera log de auditoria. | **RF-W17, RF-W39** |
| **RN-W26** | LGPD: consentimento explícito registrado com data/hora e versão dos Termos. Dados coletados limitados ao necessário para o funcionamento da plataforma (princípio da minimização). Usuário pode solicitar exclusão ou portabilidade dos dados; exclusão concluída em até 15 dias úteis. Registros financeiros históricos são anonimizados, não excluídos, para preservar integridade contábil. | **RF-W02, RF-W03** |
| **RN-W27** | O lojista deve ser notificado imediatamente ao receber um novo pedido via: (1) alerta sonoro e visual no dashboard (sempre ativo), (2) notificação do navegador (se permitido), (3) e-mail. A notificação inclui número do pedido, itens resumidos e prazo de confirmação. Disparada de forma assíncrona (fila de mensagens) para não bloquear a API de checkout. | **RF-W31, RF-W33** |
| **RN-W28** | O consumidor deve ser notificado em cada mudança de status do pedido via: (1) notificação in-app (web: push do browser; app: FCM), (2) e-mail para eventos críticos (confirmado, entregue, cancelado, reembolsado). Histórico de notificações mantido por 90 dias na interface. | **RF-W14, RF-W15, RF-W16** |

---

# 4. Regras de Negócio Mobile
Regras de negócio do aplicativo mobile: cadastro, autenticação e LGPD, catálogo e busca, carrinho e checkout, pagamento, pedido e rastreamento, devolução, entregador e geofencing.

| **Código** | **Descrição** | **Relação** |
| ---------- | ------------- | ----------- |
| **RN-M01** | O e-mail é identificador único no sistema, nenhum e-mail pode estar vinculado a mais de uma conta, independentemente do tipo (CONSUMER, STORE, DELIVERER, ADMIN). | **RF-M04** |
| **RN-M02** | Campos obrigatórios no cadastro de consumidor: nome completo, CPF válido, RG, e-mail válido (formato), senha (mín. 6 caracteres, 1 número, 1 maiúscula), CEP válido e endereço de entrega completo. Validação inline em tempo real. Confirmação de senha com verificação de igualdade em tempo real. | **RF-M04, RF-M32** |
| **RN-M03** | A tela de consentimento LGPD deve ser exibida obrigatoriamente no primeiro acesso, antes de qualquer coleta de dado ou navegação nas telas internas. Sem aceite explícito, as telas internas ficam bloqueadas. O aceite é registrado com data/hora e versão dos Termos no servidor. | **RF-M02** |
| **RN-M05** | Proteção contra força bruta no login: após 5 tentativas falhas consecutivas, o botão de login é desabilitado por 15 minutos com countdown visível. O controle é sincronizado com o servidor para evitar bypass por reinstalação do app ou troca de dispositivo. | **RF-M05, RF-M08** |
| **RN-M06** | A tela principal exibe somente lojas com status ATIVA e ABERTA (dentro do horário configurado) e dentro do raio de entrega do endereço padrão do consumidor. Lojas FECHADAS aparecem na busca com indicação de horário de abertura. Lojas INATIVAS e SUSPENSAS são completamente ocultadas. | **RF-M09, RF-M10, RF-M13** |
| **RN-M07** | Os resultados de busca e o catálogo exibem apenas produtos ATIVOS de lojas ATIVAS (abertas ou fechadas). Produtos INATIVOS e produtos de lojas INATIVAS/SUSPENSAS não aparecem nos resultados. Produtos INDISPONÍVEIS (estoque = 0) aparecem com badge de esgotado no final da listagem. | **RF-M12, RF-M13, RF-M15** |
| **RN-M08** | Ao abrir a tela de detalhe do produto, o app realiza verificação em tempo real de disponibilidade e estoque. Se o produto ficar INATIVO ou INDISPONÍVEL entre a listagem e o detalhe, o botão de carrinho é desabilitado e mensagem amigável é exibida sem redirecionar o usuário. | **RF-M14, RF-M19** |
| **RN-M09** | A busca por proximidade e o mapa de lojas usam a geolocalização do dispositivo quando a permissão é concedida. Quando negada, a busca usa o CEP do endereço padrão do consumidor como referência geográfica (geocodificado pelo servidor). O raio padrão é de 10 km, ajustável no filtro. | **RF-M09, RF-M10, RF-M13** |
| **RN-M10** | Ao exibir o detalhe do produto com um tamanho selecionado cujo estoque seja ≤ 5, o app exibe alerta de quantidade restante (ex.: 'Apenas 3 restantes neste tamanho'). Tamanhos com estoque = 0 aparecem na seleção com risco visual e são desabilitados para seleção. | **RF-M14, RF-M19** |
| **RN-M11** | A seleção de tamanho é campo obrigatório para adição ao carrinho. O botão 'Adicionar ao carrinho' permanece desabilitado até um tamanho ser selecionado. Quantidade máxima por item no carrinho é limitada ao estoque disponível do tamanho selecionado. | **RF-M14** |
| **RN-M12** | Preço promocional com vigência ativa exibe o preço original riscado, o novo preço em destaque e o percentual de desconto em badge colorido. O cálculo do desconto é feito pelo servidor; o app exibe o valor já calculado retornado pela API. | **RF-M14, RF-M16** |
| **RN-M13** | O carrinho persiste localmente em armazenamento seguro entre sessões. Ao fazer login em outro dispositivo, o carrinho é sincronizado com o servidor; em conflito por item (mesmo produto+tamanho com quantidades diferentes), prevalece o do servidor. Ao fazer logout, o carrinho local é mantido no dispositivo para reutilização no próximo login. | **RF-M17, RF-M18** |
| **RN-M14** | O app verifica disponibilidade de todos os itens do carrinho ao abrir a tela de carrinho e antes de avançar para o checkout. Itens indisponíveis são sinalizados com banner de aviso e opção de remover. Não é possível avançar para o checkout com itens indisponíveis no carrinho. | **RF-M17, RF-M19** |
| **RN-M15** | Antes de exibir o checkout, o app verifica (via API) se cada loja do carrinho realiza entrega no endereço selecionado. Lojas fora do raio são sinalizadas individualmente com aviso. O consumidor deve remover os itens da loja problemática ou selecionar outro endereço para prosseguir. | **RF-M21, RF-M22** |
| **RN-M16** | A tela de checkout exibe a estimativa de tempo de entrega por loja: soma do tempo médio de preparação configurado pelo lojista + estimativa de deslocamento do entregador. A estimativa é exibida como intervalo (ex.: '40-60 min') e é apenas indicativa. | **RF-M17, RF-M21** |
| **RN-M17** | Pedido com itens de múltiplas lojas é dividido em sub-pedidos (order splitting) pelo servidor. O consumidor paga um único valor consolidado, mas acompanha o status de cada sub-pedido independentemente. Cada sub-pedido tem seu próprio número de protocolo, entregador e prazo de confirmação. | **RF-M17, RF-M21, RF-M28** |
| **RN-M18** | O pagamento é pré-autorizado no gateway ao confirmar o pedido. A captura definitiva ocorre quando o lojista confirma. Em recusa ou timeout, a pré-autorização é liberada sem custo. O app não armazena dados completos de cartão — a tokenização é feita exclusivamente no SDK do gateway. | **RF-M23, RF-M24, RF-M25** |
| **RN-M19** | Em falha de pagamento, o app exibe a mensagem de erro fornecida pelo gateway (traduzida para linguagem amigável) sem expor códigos técnicos. PIX tem validade de 30 minutos; após expirar, o QR Code é invalidado e o app oferece opção de gerar novo código ou escolher outra forma. | **RF-M27** |
| **RN-M20** | A timeline do pedido exibe o contador regressivo de 30 minutos enquanto o status for PENDENTE, informando ao consumidor o prazo de confirmação do lojista. Se o lojista não confirmar no prazo, o pedido é automaticamente cancelado e o consumidor notificado via push e in-app. | **RF-M28** |
| **RN-M21** | O rastreamento em tempo real do entregador na etapa EM_ENTREGA usa posição geográfica enviada pelo app do entregador a cada 10 segundos. A posição é transmitida via WebSocket ao app do consumidor. (Pós-MVP) | **RF-M28** |
| **RN-M22** | Notificações push devem ser enviadas ao consumidor em cada mudança de status do pedido. Notificações de múltiplos eventos do mesmo pedido em menos de 1 minuto são agrupadas em uma única notificação consolidada. Notificações de pedidos distintos não são agrupadas. | **RF-M29** |
| **RN-M23** | A permissão de notificações push é solicitada após o primeiro login bem-sucedido do consumidor, com explicação clara do benefício ('Para avisar quando seu pedido sair para entrega'). Sem a permissão, notificações são entregues apenas in-app enquanto o app estiver aberto; funcionalidades de compra não são bloqueadas. | **RF-M29, RF-M33** |
| **RN-M26** | Permissões nativas (localização, câmera, galeria, notificações) são solicitadas exclusivamente no primeiro uso de cada recurso, com texto de justificativa exibido pelo app antes da caixa de diálogo nativa do SO. Negação de permissão desabilita somente a funcionalidade dependente, nunca o app como um todo. | **RF-M33** |
| **RN-M27** | A exclusão de conta exige confirmação em duas etapas (botão inicial + modal com digitação de 'CONFIRMAR') e dispara e-mail de confirmação ao usuário com número de protocolo. A exclusão efetiva ocorre em até 15 dias úteis. Registros de pedidos e pagamentos são anonimizados (não excluídos) para integridade contábil. | **RF-M34** |
| **RN-M28** | O entregador só recebe e pode aceitar novas entregas com status ONLINE. Ao alternar para OFFLINE, novas entregas não são ofertadas; entregas em andamento são concluídas normalmente antes do status OFFLINE ser efetivado no servidor. | **RF-M35** |
| **RN-M29** | Uma entrega é ofertada ao entregador com timeout de 60 segundos visível no app (countdown). Se o entregador não aceitar no prazo, a entrega é automaticamente ofertada ao próximo entregador disponível na região. Após 3 tentativas sem aceite, o sistema notifica o lojista e aciona o suporte. | **RF-M36** |
| **RN-M30** | Uma entrega só pode ser atribuída a um entregador por vez. Após o aceite, a entrega é removida da fila dos demais entregadores em tempo real via WebSocket. Caso o entregador abandone antes da coleta, a entrega volta à fila com prioridade elevada e o lojista é notificado. | **RF-M36** |
| **RN-M31** | Confirmação de coleta habilitada somente dentro do geofencing de 200m da loja (verificado pelo servidor com base na posição do entregador). Confirmação de entrega habilitada somente dentro do geofencing de 100m do endereço de entrega. O botão fica desabilitado fora do raio com mensagem explicativa. | **RF-M37** |
| **RN-M32** | O entregador visualiza apenas nome e endereço completo do consumidor para realizar a entrega. Número de telefone nunca é exibido em texto. Após a confirmação de entrega, os dados do consumidor ficam inacessíveis ao entregador pelo app. | **RF-M37** |
