# Etiquetas escolares - Vip Gráfica

Site de pedidos de etiquetas escolares (modelo → tema → WhatsApp).
Hospedado no GitHub Pages em https://etiquetasescolares.vipgraficalimeira.com.br

Os temas e preços são cadastrados no admin do catálogo (botão "Etiquetas escolares"); este site só lê o que foi publicado lá.

## Pedidos (área da equipe)
`pedidos.html` — lista simples dos pedidos feitos pelos clientes (tabela `pedidos_etiquetas`), só para a equipe ver o pedido e baixar a via (PNG). Login com os usuários do sistema. O acompanhamento do pedido é feito em outro sistema.

## Admin das etiquetas
`admin.html` — o administrador edita preços das cartelas, dados da loja (nome, WhatsApp, rodapé) e os temas (enviar imagens, renomear, categoria, ocultar, excluir). Os dados ficam na chave `gc2:etiquetas_publico` (independente do catálogo); se ela não existir, o site usa os dados do catálogo.
