<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cantinho do Sabor</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            /* Degradê Laranja Moderno */
            --orange-gradient: linear-gradient(135deg, #ff8c00 0%, #ff4500 100%);
            --bg-gray: #f8f9fa; 
            --text-dark: #1f1f1f;
            --text-gray: #656565;
            --white: #ffffff;
            --border: #ececec;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Inter', sans-serif; }
        body { background-color: var(--bg-gray); color: var(--text-dark); padding-bottom: 110px; }

        /* Capa Hero com Imagem do Dueto */
        .hero-banner {
            width: 100%;
            height: 220px;
            background: linear-gradient(rgba(0,0,0,0.2), rgba(0,0,0,0.4)), url('https://i.pinimg.com/736x/c6/44/0a/c6440adee5ef7fa7d38f1e6e44f28be5.jpg');
            background-size: cover;
            background-position: center;
        }

        header {
            background: var(--white);
            padding: 0 20px 24px;
            text-align: center;
            margin-top: -30px;
            border-radius: 30px 30px 0 0;
            position: relative;
            box-shadow: 0 -5px 20px rgba(0,0,0,0.05);
        }

        .logo-container {
            width: 95px;
            height: 95px;
            background: white;
            padding: 5px;
            border-radius: 50%;
            margin: 0 auto 12px;
            box-shadow: 0 8px 15px rgba(0,0,0,0.1);
            transform: translateY(-50%);
            margin-bottom: -35px;
        }

        .logo-img { width: 100%; height: 100%; border-radius: 50%; object-fit: cover; }

        .store-info h1 { font-size: 1.6rem; font-weight: 800; color: #1a1a1a; margin-top: 10px; }
        .status-badge { 
            font-size: 0.85rem; color: #2e7d32; font-weight: 600; 
            display: flex; align-items: center; justify-content: center; gap: 6px; margin-top: 8px;
        }

        /* Navegação de Categorias */
        .category-nav {
            background: var(--white);
            padding: 15px 20px;
            position: sticky;
            top: 0;
            z-index: 100;
            display: flex;
            gap: 20px;
            overflow-x: auto;
            border-bottom: 1px solid var(--border);
            scrollbar-width: none;
        }
        .category-nav::-webkit-scrollbar { display: none; }
        .cat-item { font-size: 0.95rem; font-weight: 600; color: var(--text-gray); white-space: nowrap; cursor: pointer; }
        .cat-item.active { color: #ff6a00; border-bottom: 3px solid #ff6a00; padding-bottom: 5px; }

        /* Seções e Cards */
        .container { max-width: 850px; margin: 0 auto; padding: 20px; }
        .category-section h2 { font-size: 1.3rem; margin: 25px 0 15px; font-weight: 700; color: #111; }

        .product-card {
            background: var(--white);
            border-radius: 16px;
            padding: 18px;
            margin-bottom: 14px;
            display: flex;
            justify-content: space-between;
            border: 1px solid var(--border);
            transition: transform 0.2s, box-shadow 0.2s;
            cursor: pointer;
        }
        .product-card:hover { transform: translateY(-2px); box-shadow: 0 5px 15px rgba(0,0,0,0.05); border-color: #ddd; }

        .product-content { flex: 1; padding-right: 15px; }
        .product-content h3 { font-size: 1.05rem; font-weight: 700; margin-bottom: 5px; color: #222; }
        .product-content p { font-size: 0.88rem; color: var(--text-gray); line-height: 1.4; margin-bottom: 12px; }
        .price { font-weight: 700; color: #1a1a1a; font-size: 1rem; }
        .product-image { width: 110px; height: 110px; border-radius: 12px; object-fit: cover; }

        /* Botão do Carrinho Flutuante */
        #cart-bar {
            display: none;
            position: fixed;
            bottom: 25px;
            left: 50%;
            transform: translateX(-50%);
            width: 92%;
            max-width: 480px;
            background: var(--orange-gradient);
            padding: 18px 24px;
            border-radius: 15px;
            color: white;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-weight: 700;
            box-shadow: 0 10px 30px rgba(255, 69, 0, 0.4);
            cursor: pointer;
            z-index: 1000;
        }

        /* Modal Estilizado */
        .modal { display: none; position: fixed; z-index: 2000; inset: 0; background: rgba(0,0,0,0.6); align-items: flex-end; }
        .modal-content { 
            background: var(--white); width: 100%; max-width: 600px; margin: 0 auto;
            border-radius: 25px 25px 0 0; padding: 24px; max-height: 92vh; overflow-y: auto;
        }
        
        .group-header { background: #fdf2e9; color: #d35400; padding: 12px; border-radius: 8px; font-weight: 700; font-size: 0.9rem; margin: 18px 0 10px; display: flex; justify-content: space-between; }
        .option-item { display: flex; justify-content: space-between; padding: 14px 0; border-bottom: 1px solid #f0f0f0; }
        .option-item input { width: 22px; height: 22px; accent-color: #ff4500; }

        .btn-confirm { 
            background: var(--orange-gradient); color: white; border: none; 
            width: 100%; padding: 18px; border-radius: 12px; font-weight: 700; 
            margin-top: 20px; cursor: pointer; font-size: 1rem;
        }

        #toast { 
            position: fixed; top: 30px; left: 50%; transform: translateX(-50%); 
            background: #222; color: white; padding: 14px 28px; border-radius: 50px; 
            font-weight: 600; z-index: 3000; display: none; box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }
    </style>
</head>
<body>

<div id="toast">Adicionado à sacola! 🛍️</div>

<div class="hero-banner"></div>

<header>
    <div class="logo-container">
        <img src="https://i.pinimg.com/736x/15/ac/c8/15acc8b00600f7f49f899cccbb55050d.jpg" class="logo-img">
    </div>
    <div class="store-info">
        <h1>Cantinho do Sabor</h1>
        <div class="status-badge">
            <i class="fa-solid fa-circle" style="font-size: 8px;"></i> Aberto • 15:00 às 20:00 • Entrega Grátis
        </div>
    </div>
</header>

<nav class="category-nav">
    <div class="cat-item active">Combos</div>
    <div class="cat-item">Pastéis Clássicos</div>
    <div class="cat-item">Monte o Seu</div>
    <div class="cat-item">Açaí</div>
    <div class="cat-item">Drinks</div>
</nav>

<div class="container" id="menu-area">
    <section class="category-section">
        <h2>Combos Promocionais!</h2>
        <div class="product-card" onclick="openProduct('Dueto Tradicional', 22.50, '2 Pastéis de 1 Recheio (Carne, Mussarela ou Coalho e Frango)', 'https://i.pinimg.com/736x/c6/44/0a/c6440adee5ef7fa7d38f1e6e44f28be5.jpg')">
            <div class="product-content">
                <h3>Dueto Tradicional</h3>
                <p>2 Pastéis de 1 Recheio (Carne, Mussarela ou Coalho e Frango)</p>
                <span class="price">R$ 22,50</span>
            </div>
            <img src="https://i.pinimg.com/736x/c6/44/0a/c6440adee5ef7fa7d38f1e6e44f28be5.jpg" class="product-image">
        </div>
    </section>
</div>

<div id="cart-bar" onclick="goToCheckout()">
    <span id="cart-qty">0</span>
    <span>Ver Sacola</span>
    <span id="cart-total">R$ 0,00</span>
</div>

<div id="productModal" class="modal">
    <div class="modal-content" id="modal-body"></div>
</div>

<script>
    let cart = [];
    const recheios = ["Frango", "Carne", "Pernil", "Salsicha", "Mussarela", "Coalho", "Milho", "Azeitona", "Cream Cheese", "Catupiry", "Cheddar", "Requeijão"];

    function openProduct(name, price, desc, img) {
        const modal = document.getElementById('productModal');
        const body = document.getElementById('modal-body');
        
        let customHtml = '';
        if(name.includes("Recheio")) {
            const limit = name.match(/\d+/)[0];
            customHtml = `
                <div class="group-header"><span>Escolha os recheios</span><span>Mín 1 / Máx ${limit}</span></div>
                ${recheios.map(r => `
                    <div class="option-item">
                        <span>${r}</span>
                        <input type="checkbox" name="recheio" value="${r}" onchange="limitCheck(this, ${limit})">
                    </div>
                `).join('')}
            `;
        }

        body.innerHTML = `
            <img src="${img}" style="width:100%; height:200px; object-fit:cover; border-radius:20px; margin-bottom:15px;">
            <h2 style="font-weight:800; margin-bottom:5px;">${name}</h2>
            <p style="color:var(--text-gray); font-size:0.95rem; margin-bottom:10px;">${desc}</p>
            ${customHtml}
            <button class="btn-confirm" onclick="addToCart('${name}', ${price})">Adicionar R$ ${price.toFixed(2)}</button>
            <button onclick="closeModal()" style="width:100%; background:none; border:none; padding:15px; color:var(--text-gray); font-weight:700;">Voltar</button>
        `;
        modal.style.display = 'flex';
    }

    function limitCheck(el, max) {
        const checked = document.querySelectorAll('input[name="recheio"]:checked');
        if(checked.length > max) el.checked = false;
    }

    function addToCart(name, price) {
        cart.push({name, price});
        updateUI();
        closeModal();
        const toast = document.getElementById('toast');
        toast.style.display = 'block';
        setTimeout(() => toast.style.display = 'none', 2000);
    }

    function updateUI() {
        const bar = document.getElementById('cart-bar');
        if(cart.length > 0) {
            bar.style.display = 'flex';
            document.getElementById('cart-qty').innerText = cart.length;
            const total = cart.reduce((s, i) => s + i.price, 0);
            document.getElementById('cart-total').innerText = `R$ ${total.toFixed(2)}`;
        }
    }

    function closeModal() { document.getElementById('productModal').style.display = 'none'; }

    function goToCheckout() {
        let texto = "*PEDIDO - CANTINHO DO SABOR*\n\n";
        cart.forEach(i => texto += `• ${i.name} - R$ ${i.price.toFixed(2)}\n`);
        const total = cart.reduce((s, i) => s + i.price, 0);
        texto += `\n*TOTAL: R$ ${total.toFixed(2)}*\n*ENTREGA GRÁTIS*`;
        window.open(`https://wa.me/5587933009283?text=${encodeURIComponent(texto)}`);
    }
</script>

</body>
</html>
