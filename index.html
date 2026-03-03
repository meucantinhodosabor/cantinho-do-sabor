<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cantinho do Sabor - Delivery</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --ifood-red: #ea1d2c;
            --ifood-gray: #717171;
            --ifood-light-gray: #f2f2f2;
            --text-dark: #3e3e3e;
            --success: #2e7d32;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Inter', sans-serif; }
        body { background-color: #fff; color: var(--text-dark); padding-bottom: 100px; }

        /* Header Estilo iFood */
        header { padding: 20px; text-align: center; border-bottom: 1px solid #eee; position: sticky; top: 0; background: white; z-index: 100; }
        .logo-img { width: 70px; height: 70px; border-radius: 50%; object-fit: cover; margin-bottom: 8px; border: 2px solid var(--ifood-red); }
        header h1 { font-size: 1.4rem; color: var(--ifood-red); }
        .status { font-size: 0.8rem; color: var(--success); font-weight: 600; }

        .container { max-width: 800px; margin: 0 auto; padding: 15px; }

        /* Categorias */
        h2 { font-size: 1.2rem; margin: 25px 0 15px; font-weight: 700; border-left: 4px solid var(--ifood-red); padding-left: 10px; }

        /* Cards de Produto */
        .product-card {
            display: flex; justify-content: space-between; padding: 16px; border-bottom: 1px solid #f2f2f2;
            cursor: pointer; transition: background 0.2s;
        }
        .product-card:hover { background-color: #fafafa; }
        .product-info { flex: 1; padding-right: 12px; }
        .product-info h3 { font-size: 1rem; margin-bottom: 4px; color: #333; }
        .product-info p { font-size: 0.85rem; color: var(--ifood-gray); line-height: 1.2; margin-bottom: 8px; }
        .product-price { color: var(--text-dark); font-weight: 600; font-size: 0.95rem; }
        .product-img { width: 90px; height: 90px; border-radius: 8px; object-fit: cover; background: #eee; }

        /* Modais */
        .modal { display: none; position: fixed; z-index: 1000; left: 0; top: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); }
        .modal-content { 
            background: white; position: fixed; bottom: 0; width: 100%; max-width: 600px; 
            left: 50%; transform: translateX(-50%); padding: 20px; border-radius: 20px 20px 0 0;
            max-height: 90vh; overflow-y: auto;
        }
        .recheio-item { 
            display: flex; align-items: center; justify-content: space-between; 
            padding: 12px 0; border-bottom: 1px solid #eee; 
        }
        .recheio-item input { width: 20px; height: 20px; accent-color: var(--ifood-red); }

        /* Carrinho Inferior */
        #cart-bar {
            display: none; position: fixed; bottom: 0; left: 0; width: 100%; 
            background: white; border-top: 1px solid #eee; padding: 15px 20px; z-index: 999;
        }
        .cart-btn {
            background: var(--ifood-red); color: white; display: flex; justify-content: space-between;
            padding: 14px 20px; border-radius: 8px; text-decoration: none; font-weight: bold;
        }

        /* Formulário Checkout */
        .form-group { margin-bottom: 12px; }
        .form-group label { display: block; font-size: 0.85rem; margin-bottom: 4px; color: var(--ifood-gray); }
        .form-group input, .form-group select { 
            width: 100%; padding: 10px; border: 1px solid #ddd; border-radius: 8px; outline: none;
        }

        .btn-confirm { background: var(--ifood-red); color: white; border: none; width: 100%; padding: 15px; border-radius: 8px; font-weight: bold; margin-top: 10px; cursor: pointer; }
    </style>
</head>
<body>

<header>
    <img src="1000232949.jpg" class="logo-img" alt="Logo">
    <h1>Cantinho do Sabor</h1>
    <p class="status">● Aberto agora</p>
</header>

<div class="container">
    <h2>Pastéis</h2>
    <div class="product-card" onclick="openModal('Pastel', 19.50, 'recheios')">
        <div class="product-info">
            <h3>Pastel Personalizado</h3>
            <p>Escolha exatamente 3 recheios de sua preferência.</p>
            <span class="product-price">R$ 19,50</span>
        </div>
        <img src="https://via.placeholder.com/100?text=Pastel" class="product-img">
    </div>

    <h2>Cuscuz</h2>
    <div class="product-card" onclick="openModal('Cuscuz', 18.50, 'recheios')">
        <div class="product-info">
            <h3>Cuscuz Recheado</h3>
            <p>Escolha 3 recheios. Acompanha manteiga.</p>
            <span class="product-price">R$ 18,50</span>
        </div>
        <img src="https://via.placeholder.com/100?text=Cuscuz" class="product-img">
    </div>

    <h2>Bebidas</h2>
    <div class="product-card" onclick="addSimpleItem('Coca-Cola Lata', 5.00)">
        <div class="product-info">
            <h3>Coca-Cola Lata</h3>
            <p>350ml gelada.</p>
            <span class="product-price">R$ 5,00</span>
        </div>
        <img src="https://via.placeholder.com/100?text=Coca" class="product-img">
    </div>
</div>

<div id="recheioModal" class="modal">
    <div class="modal-content">
        <h3 id="modalTitle">Escolha 3 recheios</h3>
        <p style="color: var(--ifood-red); font-size: 0.8rem; margin-bottom: 10px;">Obrigatório selecionar 3</p>
        <div id="recheiosList">
            </div>
        <button class="btn-confirm" onclick="confirmRecheios()">Adicionar</button>
        <button onclick="closeModal('recheioModal')" style="width:100%; background:none; border:none; padding:10px; color:var(--ifood-gray);">Voltar</button>
    </div>
</div>

<div id="checkoutModal" class="modal">
    <div class="modal-content">
        <h3>Finalizar Pedido</h3>
        <div id="cartItemsList" style="margin: 15px 0; font-size: 0.9rem; border-bottom: 1px solid #eee;"></div>
        
        <div class="form-group">
            <label>Seu Nome</label>
            <input type="text" id="nome" placeholder="Ex: João Silva">
        </div>
        <div class="form-group">
            <label>Endereço Completo</label>
            <input type="text" id="endereco" placeholder="Rua, número e bairro">
        </div>
        <div class="form-group">
            <label>Forma de Pagamento</label>
            <select id="pagamento">
                <option value="Pix">Pix</option>
                <option value="Cartão">Cartão</option>
                <option value="Dinheiro">Dinheiro</option>
            </select>
        </div>
        <button class="btn-confirm" onclick="enviarWhatsApp()">Enviar para o WhatsApp</button>
        <button onclick="closeModal('checkoutModal')" style="width:100%; background:none; border:none; padding:10px; color:var(--ifood-gray);">Continuar Comprando</button>
    </div>
</div>

<div id="cart-bar">
    <div class="cart-btn" onclick="openCheckout()">
        <span><i class="fa-solid fa-bag-shopping"></i> <span id="cart-qty">0</span></span>
        <span>Ver sacola</span>
        <span id="cart-total">R$ 0,00</span>
    </div>
</div>

<script>
    let cart = [];
    let currentItem = null;
    const listaRecheios = ["Carne", "Queijo", "Frango", "Calabresa", "Presunto", "Ovo", "Milho", "Azeitona"];

    function openModal(name, price) {
        currentItem = { name, price };
        const list = document.getElementById('recheiosList');
        list.innerHTML = '';
        listaRecheios.forEach(r => {
            list.innerHTML += `
                <label class="recheio-item">
                    <span>${r}</span>
                    <input type="checkbox" name="recheio" value="${r}" onchange="checkLimit(this)">
                </label>
            `;
        });
        document.getElementById('recheioModal').style.display = 'block';
    }

    function checkLimit(el) {
        const checked = document.querySelectorAll('input[name="recheio"]:checked');
        if (checked.length > 3) {
            el.checked = false;
            alert("Escolha apenas 3 recheios!");
        }
    }

    function confirmRecheios() {
        const checked = Array.from(document.querySelectorAll('input[name="recheio"]:checked')).map(i => i.value);
        if (checked.length !== 3) {
            alert("Você precisa escolher exatamente 3 recheios!");
            return;
        }
        addSimpleItem(`${currentItem.name} (${checked.join(', ')})`, currentItem.price);
        closeModal('recheioModal');
    }

    function addSimpleItem(name, price) {
        cart.push({ name, price });
        updateCartBar();
    }

    function updateCartBar() {
        const bar = document.getElementById('cart-bar');
        if (cart.length > 0) {
            bar.style.display = 'block';
            document.getElementById('cart-qty').innerText = cart.length;
            const total = cart.reduce((acc, i) => acc + i.price, 0);
            document.getElementById('cart-total').innerText = `R$ ${total.toFixed(2)}`;
        }
    }

    function openCheckout() {
        const list = document.getElementById('cartItemsList');
        list.innerHTML = cart.map(i => `<div style="display:flex; justify-content:space-between; margin-bottom:5px;"><span>${i.name}</span> <b>R$ ${i.price.toFixed(2)}</b></div>`).join('');
        document.getElementById('checkoutModal').style.display = 'block';
    }

    function enviarWhatsApp() {
        const nome = document.getElementById('nome').value;
        const endereco = document.getElementById('endereco').value;
        const pag = document.getElementById('pagamento').value;

        if (!nome || !endereco) { alert("Preencha nome e endereço!"); return; }

        let texto = `*NOVO PEDIDO - CANTINHO DO SABOR*\n--------------------------\n`;
        texto += `*Cliente:* ${nome}\n*Endereço:* ${endereco}\n*Pagamento:* ${pag}\n\n*ITENS:*\n`;
        
        cart.forEach(i => { texto += `• ${i.name} - R$ ${i.price.toFixed(2)}\n`; });
        
        const total = cart.reduce((acc, i) => acc + i.price, 0);
        texto += `\n*TOTAL: R$ ${total.toFixed(2)}*`;

        const fone = "5587933009283";
        window.open(`https://wa.me/${fone}?text=${encodeURIComponent(texto)}`);
    }

    function closeModal(id) { document.getElementById(id).style.display = 'none'; }
</script>

</body>
</html>
