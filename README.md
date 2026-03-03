<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cantinho do Sabor</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        :root {
            --orange-gradient: linear-gradient(135deg, #ff8c00 0%, #ff4500 100%);
            --bg-gray: #f8f9fa; --text-dark: #1f1f1f; --text-gray: #656565; --white: #ffffff; --border: #ececec;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Inter', sans-serif; }
        body { background-color: var(--bg-gray); color: var(--text-dark); padding-bottom: 110px; }

        /* Capa Hero */
        .hero-banner {
            width: 100%; height: 220px;
            background: linear-gradient(rgba(0,0,0,0.2), rgba(0,0,0,0.4)), url('https://i.pinimg.com/736x/c6/44/0a/c6440adee5ef7fa7d38f1e6e44f28be5.jpg');
            background-size: cover; background-position: center;
        }

        header {
            background: var(--white); padding: 0 20px 24px; text-align: center;
            margin-top: -30px; border-radius: 30px 30px 0 0; position: relative;
            box-shadow: 0 -5px 20px rgba(0,0,0,0.05);
        }

        .logo-container {
            width: 95px; height: 95px; background: white; padding: 5px;
            border-radius: 50%; margin: 0 auto 12px; transform: translateY(-50%);
            box-shadow: 0 8px 15px rgba(0,0,0,0.1); margin-bottom: -35px;
        }

        .logo-img { width: 100%; height: 100%; border-radius: 50%; object-fit: cover; }
        .status-badge { font-size: 0.85rem; color: #2e7d32; font-weight: 600; margin-top: 8px; }

        /* Navegação Categorias */
        .category-nav {
            background: var(--white); padding: 15px 20px; position: sticky; top: 0;
            z-index: 100; display: flex; gap: 20px; overflow-x: auto; border-bottom: 1px solid var(--border);
        }
        .cat-item { font-size: 0.95rem; font-weight: 600; color: var(--text-gray); white-space: nowrap; cursor: pointer; }
        .cat-item.active { color: #ff6a00; border-bottom: 3px solid #ff6a00; padding-bottom: 5px; }

        /* Container Produtos */
        .container { max-width: 850px; margin: 0 auto; padding: 20px; }
        .product-card {
            background: var(--white); border-radius: 16px; padding: 18px; margin-bottom: 14px;
            display: flex; justify-content: space-between; border: 1px solid var(--border); cursor: pointer;
        }
        .product-image { width: 100px; height: 100px; border-radius: 12px; object-fit: cover; }

        /* Barra de Carrinho */
        #cart-bar {
            display: none; position: fixed; bottom: 25px; left: 50%; transform: translateX(-50%);
            width: 92%; max-width: 480px; background: var(--orange-gradient);
            padding: 18px 24px; border-radius: 15px; color: white;
            justify-content: space-between; align-items: center; font-weight: 700; z-index: 1000; cursor: pointer;
        }

        /* Modais */
        .modal { display: none; position: fixed; z-index: 2000; inset: 0; background: rgba(0,0,0,0.6); align-items: flex-end; }
        .modal-content { 
            background: var(--white); width: 100%; max-width: 600px; margin: 0 auto;
            border-radius: 25px 25px 0 0; padding: 24px; max-height: 90vh; overflow-y: auto;
        }
        
        /* Formulário Checkout */
        .form-group { margin-bottom: 15px; }
        .form-group label { display: block; font-weight: 600; font-size: 0.9rem; margin-bottom: 5px; }
        .form-group input, .form-group select { 
            width: 100%; padding: 12px; border: 1px solid #ddd; border-radius: 8px; font-size: 1rem;
        }

        .pix-box { 
            background: #fdf2e9; border: 1px dashed #ff8c00; padding: 15px; border-radius: 10px; 
            margin: 15px 0; display: none; text-align: center;
        }

        .btn-action { 
            background: var(--orange-gradient); color: white; border: none; 
            width: 100%; padding: 18px; border-radius: 12px; font-weight: 700; cursor: pointer;
        }

        /* Itens do Carrinho dentro do Modal */
        .cart-item-row { display: flex; justify-content: space-between; align-items: center; padding: 10px 0; border-bottom: 1px solid #eee; }
        .qty-controls { display: flex; align-items: center; gap: 10px; }
        .qty-btn { width: 25px; height: 25px; border-radius: 50%; border: 1px solid #ff8c00; background: white; color: #ff8c00; font-weight: bold; cursor: pointer; }
    </style>
</head>
<body>

<div class="hero-banner"></div>

<header>
    <div class="logo-container">
        <img src="https://i.pinimg.com/736x/15/ac/c8/15acc8b00600f7f49f899cccbb55050d.jpg" class="logo-img">
    </div>
    <div class="store-info">
        <h1>Cantinho do Sabor</h1>
        <div class="status-badge">● Aberto • 15:00 às 20:00</div>
    </div>
</header>

<div class="category-nav">
    <div class="cat-item active">Cardápio Completo</div>
</div>

<div class="container" id="menu-area">
    </div>

<div id="cart-bar" onclick="openCheckoutModal()">
    <span id="cart-qty">0</span>
    <span>Ver Sacola</span>
    <span id="cart-total">R$ 0,00</span>
</div>

<div id="checkoutModal" class="modal">
    <div class="modal-content">
        <h2 style="margin-bottom: 15px;">Sua Sacola</h2>
        <div id="cart-items-list"></div>
        
        <h3 style="margin: 20px 0 10px;">Dados para Entrega</h3>
        <form id="checkoutForm">
            <div class="form-group"><label>Nome Completo *</label><input type="text" id="cust-name" required></div>
            <div class="form-group"><label>Endereço e Número *</label><input type="text" id="cust-address" required></div>
            <div class="form-group"><label>Ponto de Referência *</label><input type="text" id="cust-ref" required></div>
            <div class="form-group">
                <label>Forma de Pagamento *</label>
                <select id="cust-payment" onchange="togglePix()" required>
                    <option value="">Selecione...</option>
                    <option value="Dinheiro">Dinheiro</option>
                    <option value="Cartão">Cartão</option>
                    <option value="Pix">Pix</option>
                </select>
            </div>

            <div id="pix-area" class="pix-box">
                <p style="font-size: 0.8rem; margin-bottom: 5px;">Chave Pix (Copia e Cola):</p>
                <strong id="pix-key" style="font-size: 0.7rem; word-break: break-all;">82e5f2e0-772e-46d6-8ec9-3dbcf9b2c54c</strong><br>
                <button type="button" onclick="copyPix()" style="margin-top:10px; font-size: 0.7rem;">Copiar Chave</button>
            </div>

            <div style="margin: 15px 0; font-weight: 700; font-size: 1.2rem; text-align: right;">
                Total: <span id="form-total">R$ 0,00</span>
            </div>

            <button type="submit" class="btn-action">FINALIZAR PEDIDO NO WHATSAPP</button>
        </form>
        <button onclick="closeModal()" style="width:100%; background:none; border:none; padding:15px; color:var(--text-gray);">Continuar Comprando</button>
    </div>
</div>

<script>
    // Configurações e Dados
    const WHATSAPP_NUM = "5587933009283";
    const PIX_KEY = "82e5f2e0-772e-46d6-8ec9-3dbcf9b2c54c";
    
    let cart = JSON.parse(localStorage.getItem('cart')) || [];

    const products = [
        {n: 'Dueto Tradicional', p: 22.50, d: '2 Pastéis de 1 Recheio', img: 'https://i.pinimg.com/736x/c6/44/0a/c6440adee5ef7fa7d38f1e6e44f28be5.jpg'},
        {n: 'Caipira Especial', p: 17.50, d: 'Frango e Milho', img: 'https://i.pinimg.com/736x/54/f3/3e/54f33e374276eb01904b8a7bfe94081e.jpg'},
        {n: 'O Queridinho', p: 17.50, d: 'Carne e Queijo', img: 'https://i.pinimg.com/736x/0e/ba/e1/0ebae10f386aaf02dda228b58951ce41.jpg'},
        {n: 'Pastel 2 Recheios', p: 17.50, d: 'Monte o seu', img: 'https://i.pinimg.com/736x/01/4e/04/014e04188feecfd5ea2ac209eb3ad09b.jpg'},
        {n: 'Batidinha de Uva', p: 7.50, d: '300ml', img: 'https://i.pinimg.com/736x/12/99/22/1299226e7417a8c5bcdaf7d21a0ac45e.jpg'}
        // Adicione todos os outros itens aqui seguindo este padrão
    ];

    // Funções do Site
    function renderMenu() {
        const area = document.getElementById('menu-area');
        area.innerHTML = products.map((prod, index) => `
            <div class="product-card" onclick="addToCart(${index})">
                <div class="product-content">
                    <h3>${prod.n}</h3>
                    <p>${prod.d}</p>
                    <span class="price">R$ ${prod.p.toFixed(2)}</span>
                </div>
                <img src="${prod.img}" class="product-image">
            </div>
        `).join('');
    }

    function addToCart(index) {
        const item = products[index];
        const existing = cart.find(c => c.n === item.n);
        if(existing) {
            existing.q++;
        } else {
            cart.push({ n: item.n, p: item.p, q: 1 });
        }
        updateCart();
        alert(`${item.n} adicionado!`);
    }

    function updateCart() {
        localStorage.setItem('cart', JSON.stringify(cart));
        const totalQty = cart.reduce((acc, i) => acc + i.q, 0);
        const totalPrice = cart.reduce((acc, i) => acc + (i.p * i.q), 0);
        
        document.getElementById('cart-bar').style.display = totalQty > 0 ? 'flex' : 'none';
        document.getElementById('cart-qty').innerText = totalQty;
        document.getElementById('cart-total').innerText = `R$ ${totalPrice.toFixed(2)}`;
        document.getElementById('form-total').innerText = `R$ ${totalPrice.toFixed(2)}`;
    }

    function openCheckoutModal() {
        const list = document.getElementById('cart-items-list');
        list.innerHTML = cart.map((item, idx) => `
            <div class="cart-item-row">
                <div><strong>${item.n}</strong><br><small>R$ ${item.p.toFixed(2)}</small></div>
                <div class="qty-controls">
                    <button class="qty-btn" onclick="changeQty(${idx}, -1)">-</button>
                    <span>${item.q}</span>
                    <button class="qty-btn" onclick="changeQty(${idx}, 1)">+</button>
                </div>
            </div>
        `).join('');
        document.getElementById('checkoutModal').style.display = 'flex';
    }

    function changeQty(idx, delta) {
        cart[idx].q += delta;
        if(cart[idx].q <= 0) cart.splice(idx, 1);
        updateCart();
        openCheckoutModal();
        if(cart.length === 0) closeModal();
    }

    function togglePix() {
        const pay = document.getElementById('cust-payment').value;
        document.getElementById('pix-area').style.display = (pay === 'Pix') ? 'block' : 'none';
    }

    function copyPix() {
        navigator.clipboard.writeText(PIX_KEY);
        alert("Chave Pix Copiada!");
    }

    function closeModal() { document.getElementById('checkoutModal').style.display = 'none'; }

    // Finalização via WhatsApp
    document.getElementById('checkoutForm').onsubmit = function(e) {
        e.preventDefault();
        
        const name = document.getElementById('cust-name').value;
        const addr = document.getElementById('cust-address').value;
        const ref = document.getElementById('cust-ref').value;
        const pay = document.getElementById('cust-payment').value;
        const total = cart.reduce((acc, i) => acc + (i.p * i.q), 0);

        let itensTexto = "";
        cart.forEach(i => itensTexto += ` - ${i.q}x ${i.n} (R$ ${(i.p * i.q).toFixed(2)})\n`);

        const mensagem = `*NOVO PEDIDO - CANTINHO DO SABOR*\n\n` +
            `*Cliente:* ${name}\n` +
            `*Endereço:* ${addr}\n` +
            `*Referência:* ${ref}\n` +
            `*Pagamento:* ${pay}\n\n` +
            `*ITENS:*\n${itensTexto}\n` +
            `*TOTAL: R$ ${total.toFixed(2)}*\n\n` +
            `_Pedido feito via site oficial._`;

        window.open(`https://wa.me/${WHATSAPP_NUM}?text=${encodeURIComponent(mensagem)}`);
        
        // Limpa carrinho após pedido
        cart = [];
        updateCart();
        closeModal();
    };

    renderMenu();
    updateCart();
</script>

</body>
</html>
