# Etiquetas escolares - Vip Gráfica

Site de pedidos de etiquetas escolares (modelo → tema → WhatsApp).
Hospedado no GitHub Pages em https://etiquetasescolares.vipgraficalimeira.com.br

Os temas e preços são cadastrados no admin do catálogo (botão "Etiquetas escolares"); este site só lê o que foi publicado lá.

## Pedidos (área da equipe)
`pedidos.html` — lista simples dos pedidos feitos pelos clientes (tabela `pedidos_etiquetas`), só para a equipe ver o pedido e baixar a via (PNG). Login com os usuários do sistema. O acompanhamento do pedido é feito em outro sistema.

## Admin das etiquetas
`admin.html` — o administrador edita preços das cartelas, dados da loja (nome, WhatsApp, rodapé) e os temas (enviar imagens, renomear, categoria, ocultar, excluir). Os dados ficam na chave `gc2:etiquetas_publico` (independente do catálogo); se ela não existir, o site usa os dados do catálogo.

## Quadro de etapas (kanban)
`pedidos.html` abre num quadro com as etapas Novo · Arte · Produção · Expedição · Entregue. O cartão anda pelos botões ou arrastando. Voltar da Expedição para a Produção exige motivo (o banco recusa sem motivo) e o cartão fica marcado em vermelho. O botão "Lista" volta para a visão antiga. O CPF aparece no cartão quando o pedido está em Expedição ou Entregue, para conferir na retirada.

### Quem move o quê
Cada pessoa faz um movimento só, e tem um link direto da etapa dela (abre em lista grande, com um botão por pedido e seleção em lote):
- Vendedora: `pedidos.html?etapa=novo`
- Arte (só pedidos com tema personalizado): `pedidos.html?etapa=arte`
- Produção: `pedidos.html?etapa=producao`
- Expedição: `pedidos.html?etapa=expedicao`

A etapa Arte é pulada automaticamente quando o pedido não tem tema personalizado: de Novo vai direto para Produção.
O quadro completo continua em `pedidos.html`.

### Excluir pedido
Só administrador (role `admin` no cadastro de usuários) vê o botão **Excluir**, no cartão do quadro e na tela de cada etapa. Pede duas confirmações e apaga de vez — não tem como recuperar. A regra está no banco (`pedidos_etq_admin_delete` usando `vip_eh_admin()`), então quem não é admin não apaga nem por fora da tela.
