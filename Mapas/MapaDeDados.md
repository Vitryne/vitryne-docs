# Mapa de Dados  
**(entidades e relações em linguagem natural)**

**Usuários e Autenticação**  
"Um usuário tem um endereço"  
"Um usuário tem um e-mail único"  
"Um usuário tem uma senha criptografada"  
"Um usuário tem um CPF único"  
"Um token de verificação pertence a um usuário"  
"Um usuário tem um status de conta (ativo/inativo/suspenso)"

**Loja**  
"Uma loja tem um CNPJ único"  
"Uma loja tem um endereço"  
"Uma loja tem um catálogo"  
"Uma loja tem dados bancários"  
"Uma loja tem um status (aberta/fechada/suspensa)"  
"Uma loja tem várias avaliações"

**Produto**  
"Um produto pertence a uma loja"  
"Um produto tem várias fotos"  
"Um produto tem várias variações de tamanho"  
"Um produto tem uma categoria"  
"Um produto tem um estoque"  
"Um produto tem um status (disponível/indisponível)"

**Catálogo e Busca**  
"Um catálogo pertence a uma loja"  
"Um catálogo tem vários produtos"  
"Uma categoria tem vários produtos"  
"Um filtro pertence a uma categoria"

**Carrinho**  
"Um carrinho tem vários itens"  
"Um item de carrinho pertence a um produto"  
"Um item de carrinho tem uma quantidade"  
"Um item de carrinho tem uma variação de tamanho escolhida"  
"Um carrinho pertence a um cliente"

**Pedido**  
"Um pedido tem um status (aguardando/confirmado/em entrega/entregue/cancelado)"  
"Um pedido tem um endereço de entrega"  
"Um pedido pertence a uma loja"  
"Um pedido tem vários itens"  
"Um item de pedido pertence a um produto"  
"Um item de pedido tem uma quantidade"  
"Um item de pedido tem um preço registrado no momento da compra"

**Pagamento**  
"Um pagamento tem um status (pendente/aprovado/recusado/estornado)"  
"Um pagamento tem um método (cartão/pix/boleto)"  
"Um pagamento tem uma data de aprovação"  
"Um reembolso pertence a um pagamento"  
"Um reembolso tem um status (solicitado/processado)"

**Entrega**  
"Uma entrega pertence a um pedido"  
"Uma entrega tem um status (aguardando coleta/em rota/entregue/devolução)"  
"Uma entrega tem um endereço de coleta"  
"Uma entrega tem um endereço de destino"  
"Uma entrega tem uma data estimada"

**Devolução (diferencial do projeto)**  
"Uma devolução pertence a um pedido"  
"Uma devolução tem um motivo"  
"Uma devolução tem um status (solicitada/coletada/recebida pela loja/reembolso liberado)"  
"Uma devolução tem um prazo limite"  
"Uma devolução tem uma entrega associada"  
"Uma devolução gera um reembolso"

**Notificações**  
"Uma notificação pertence a um usuário"  
"Uma notificação tem um tipo (novo pedido/status de entrega/pagamento/devolução)"  
"Uma notificação tem um status (lida/não lida)"  
**Avaliações**  
"Uma avaliação pertence a um pedido"  
"Uma avaliação pertence a um cliente"  
"Uma avaliação pode ser de um produto ou de uma loja"  
"Uma avaliação tem uma nota"  
"Uma avaliação tem um comentário"