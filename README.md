<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cantinho do Sabor</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;800&display=swap" rel="stylesheet">
    <style>
        :root {
            --orange: linear-gradient(135deg, #ff8c00 0%, #ff4500 100%);
            --bg: #f8f9fa; --white: #ffffff; --text: #1a1a1a;
        }
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Inter', sans-serif; }
        body { background: var(--bg); color: var(--text); padding-bottom: 100px; }
        
        .hero { width: 100%; height: 180px; background: url('https://i.pinimg.com/736x/c6/44/0a/c6440adee5ef7fa7d38f1e6e44f28be5.jpg') center/cover; }
        header { background: var(--white); padding: 20px; text-align: center; margin-top: -30px; border-radius: 30px 30px 0 0; box-shadow: 0 -5px 15px rgba(0,0,0,0.05); }
        .logo { width: 80px; height: 80px; border-radius: 50%; border: 4px solid var(--white); margin-top: -60px; object-fit: cover; }
        
        .nav-cats { display: flex; gap: 10px; overflow-x: auto; padding: 15px; background: var(--white); position: sticky; top: 0; z-index: 10; border-bottom: 1px solid #eee; }
        .cat-btn { padding: 8px 15px; border-radius: 20px; border: 1px solid #ddd; background: var(--white); white-space: nowrap; cursor: pointer; font-weight: 600; font-size: 0.8rem; }
        .cat-btn.active { background: #ff4500; color: white; border-color: #ff4500; }

        .container { max-width: 600px; margin: 0 auto; padding: 15px; }
        .card { background: var(--white); border-radius: 15px; padding: 15px; margin-bottom: 12px; display: flex; align-items: center; justify-content: space-between; cursor: pointer; border: 1px solid #eee; }
        .card-info { flex: 1; }
        .card-info h3 { font-size: 0.95rem; margin-bottom: 5px; }
        .card-info p { font-size: 0.75rem; color: #666; margin-bottom: 8px; }
        .price { color: #ff4500; font-weight: 700; }
        .card-img { width: 70px; height: 70px; border-radius: 10px; object-fit: cover; margin-left: 10px; }

        #cart-bar { display: none; position: fixed; bottom: 20px; left: 50%; transform: translateX(-50%); width: 90%; max-width: 500px; background: var(--orange); color: white; padding: 15px 20px; border-radius: 12px; justify-content: space-between; font-weight: 700; z-index: 1000; cursor: pointer; }

        .modal { display: none; position: fixed; inset: 0; background: rgba(0,0,0,0.7); z-index: 2000; align-items: flex-end; }
        .modal-content { background: white; width: 100%; max-width: 500px; margin: 0 auto; border-radius: 20px 20px 0 0; padding: 20px; max-height: 90vh; overflow-y: auto; }
        
        .form-group { margin-bottom: 12px; }
        .form-group label { display: block; font-size: 0.8rem; font-weight: 700; margin-bottom: 5px; }
        .form-group input, .form-group select { width: 100%; padding: 12px; border: 1px solid #ddd; border-radius: 8px; }
        
        .btn-add { background: var(--orange); color: white; border: none; width: 100%; padding: 15px; border-radius: 10px; font-weight: 700; cursor: pointer; margin-top: 10px; }
        .btn-add:disabled { opacity: 0.5; cursor: not-allowed; }
        .opt-box { background: #f9f9f9; padding: 10px; border-radius: 8px; margin-bottom: 10px; cursor: pointer; border: 1px solid #eee; }
        .opt-box.selected { background: #ff4500; color: white; border-color: #ff4500; }
        .size-selector { display: flex; gap: 10px; margin-bottom: 15px; }
        .size-btn { flex: 1; padding: 10px; border: 1px solid #ddd; border-radius: 8px; background: white; cursor: pointer; text-align: center; }
        .size-btn.selected { background: #ff4500; color: white; border-color: #ff4500; }
        .combo-grid { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 8px; margin: 15px 0; }
        .combo-option { border: 1px solid #eee; padding: 10px; border-radius: 8px; text-align: center; cursor: pointer; }
        .combo-option.selected { background: #ff4500; color: white; }
        .recheios-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin: 15px 0; max-height: 300px; overflow-y: auto; }
        .recheio-item { display: flex; align-items: center; gap: 5px; font-size: 0.8rem; }
    </style>
</head>
<body>

<div class="hero"></div>
<header>
    <img src="https://i.pinimg.com/736x/15/ac/c8/15acc8b00600f7f49f899cccbb55050d.jpg" class="logo">
    <h1 style="font-size: 1.3rem; margin-top: 10px;">Cantinho do Sabor</h1>
    <p style="font-size: 0.8rem; color: #2e7d32; font-weight: 700;">● Aberto • Delivery via WhatsApp</p>
</header>

<div class="nav-cats" id="cat-nav">
    <button class="cat-btn active" onclick="filter('todos')">Todos</button>
    <button class="cat-btn" onclick="filter('combos')">Combos</button>
    <button class="cat-btn" onclick="filter('acai')">Açaí Gourmet</button>
    <button class="cat-btn" onclick="filter('classicos')">Clássicos</button>
    <button class="cat-btn" onclick="filter('monte')">Monte o Seu</button>
    <button class="cat-btn" onclick="filter('cuscuz')">Cuscuz</button>
    <button class="cat-btn" onclick="filter('tapioca')">Tapioca</button>
    <button class="cat-btn" onclick="filter('porcoes')">Porções</button>
    <button class="cat-btn" onclick="filter('bebidas')">Bebidas</button>
    <button class="cat-btn" onclick="filter('novidades')">Novidades</button>
</div>

<div class="container" id="menu"></div>

<div id="cart-bar" onclick="showCart()">
    <span id="c-qty">0</span>
    <span>Ver Sacola</span>
    <span id="c-total">R$ 0,00</span>
</div>

<div id="modal-custom" class="modal"><div class="modal-content" id="custom-body"></div></div>
<div id="modal-cart" class="modal">
    <div class="modal-content">
        <h2>Sua Sacola</h2>
        <div id="cart-list" style="margin: 15px 0;"></div>
        <hr><br>
        <form id="f-checkout">
            <div class="form-group"><label>Nome *</label><input type="text" id="f-nome" required></div>
            <div class="form-group"><label>Endereço e Número *</label><input type="text" id="f-rua" required></div>
            <div class="form-group"><label>Referência *</label><input type="text" id="f-ref" required></div>
            <div class="form-group">
                <label>Pagamento *</label>
                <select id="f-pay" onchange="checkPix()" required>
                    <option value="">Escolha...</option>
                    <option value="Pix">Pix</option>
                    <option value="Dinheiro">Dinheiro</option>
                    <option value="Cartão">Cartão</option>
                </select>
            </div>
            <div id="pix-info" style="display:none; background:#fff5eb; padding:10px; border:1px dashed #ff4500; text-align:center; font-size:0.7rem; border-radius:8px;">
                Chave Pix: <strong>82e5f2e0-772e-46d6-8ec9-3dbcf9b2c54c</strong><br>
                <button type="button" onclick="navigator.clipboard.writeText('82e5f2e0-772e-46d6-8ec9-3dbcf9b2c54c');alert('Copiado!')">Copiar Chave</button>
            </div>
            <h3 style="text-align:right; margin:15px 0;">Total: <span id="f-total">R$ 0,00</span></h3>
            <button type="submit" class="btn-add">FINALIZAR NO WHATSAPP</button>
        </form>
        <button onclick="closeAll()" style="width:100%; border:none; background:none; padding:10px; color:#666;">Voltar</button>
    </div>
</div>

<script>
    const TEL = "5587933009283";
    let cart = [];
    let currentItem = null;
    let selectedSize = null;
    let selectedPrice = null;
    let selectedCombo = null;
    let selectedRecheios = [];

    const recheios = [
        "Frango", "Carne", "Pernil", "Salsicha", "Mussarela", "Coalho", 
        "Milho", "Azeitona", "Cream Cheese", "Requeijão", "Cheddar", 
        "Catupiry", "Alho Frito", "Pimenta Calabresa"
    ];

    const db = [
        // Combos
        {id:1, nome:'Dueto Tradicional', preco:22.50, desc:'2 Pastéis (Carne, Frango, Mussarela ou Coalho)', cat:'combos', img:'https://i.pinimg.com/736x/c6/44/0a/c6440adee5ef7fa7d38f1e6e44f28be5.jpg', tipo:'dueto'},
        
        // Açaí Gourmet
        {id:2, nome:'Batidinha de Açaí 300ml', preco:14.90, cat:'acai', img:'https://i.pinimg.com/736x/cf/3e/ce/cf3eced59ad15ee6fc1ffb3ebe057cd6.jpg', tipo:'acai'},
        {id:3, nome:'Batidinha de Açaí 500ml', preco:22.00, cat:'acai', img:'https://i.pinimg.com/736x/cf/3e/ce/cf3eced59ad15ee6fc1ffb3ebe057cd6.jpg', tipo:'acai'},
        
        // Clássicos
        {id:4, nome:'Caipira Especial', preco:17.50, desc:'Frango/Milho', cat:'classicos', img:'https://i.pinimg.com/736x/54/f3/3e/54f33e374276eb01904b8a7bfe94081e.jpg'},
        {id:5, nome:'O Queridinho', preco:17.50, desc:'Carne/Queijo', cat:'classicos', img:'https://i.pinimg.com/736x/0e/ba/e1/0ebae10f386aaf02dda228b58951ce41.jpg'},
        {id:6, nome:'Pastel de Hotdog', preco:17.50, desc:'Salsicha/Carne/Cheddar', cat:'classicos', img:'https://i.pinimg.com/736x/f6/ae/90/f6ae90345dc56319aa73d830743edb7f.jpg'},
        {id:7, nome:'Frango Dourado', preco:18.00, desc:'Frango/Queijo', cat:'classicos', img:'https://i.pinimg.com/736x/90/7b/a5/907ba5cb7574a1ad9aa2eb0548c9eed4.jpg'},
        {id:8, nome:'Sabor Mediterrâneo', preco:18.00, desc:'Carne/Azeitonas', cat:'classicos', img:'https://i.pinimg.com/736x/8f/f6/b2/8ff6b260aa8709cce002ec39f97a464c.jpg'},
        {id:9, nome:'Super Cremoso', preco:18.50, desc:'Frango/Requeijão', cat:'classicos', img:'https://i.pinimg.com/736x/66/20/80/662080576d5755f1fb79d243117a37d8.jpg'},
        {id:10, nome:'Frango Clássico', preco:18.50, desc:'Frango/Catupiry/Milho', cat:'classicos', img:'https://i.pinimg.com/736x/f4/29/44/f42944f3d798cf35a1e4fb028e62813a.jpg'},
        {id:11, nome:'Cheddar Melt', preco:18.50, desc:'Carne/Cheddar', cat:'classicos', img:'https://i.pinimg.com/736x/3b/ee/28/3bee28d4d4e562a48782b3c1371d4009.jpg'},
        {id:12, nome:'Trio Imperial', preco:18.50, desc:'3 Queijos', cat:'classicos', img:'https://i.pinimg.com/736x/25/44/bb/2544bb486fc56f83130814b41c27b0a9.jpg'},
        {id:13, nome:'Pernil Cremoso', preco:19.50, desc:'Pernil/Catupiry/Milho', cat:'classicos', img:'https://i.pinimg.com/736x/ee/65/0e/ee650e334bd5020ba51dfa1b32043d60.jpg'},
        {id:14, nome:'Pernil Especial', preco:20.00, desc:'Pernil/Coalho/Requeijão', cat:'classicos', img:'https://i.pinimg.com/736x/de/29/bf/de29bf0cfd6c1b1b2a52e37ea4e05c07.jpg'},
        {id:15, nome:'Frango Gourmet', preco:20.00, desc:'Cream Cheese/Azeitona', cat:'classicos', img:'https://i.pinimg.com/736x/fb/c8/f4/fbc8f415a71bfb628aed9f182affe245.jpg'},
        {id:16, nome:'Carne Completa', preco:20.00, desc:'Queijo/Milho/Azeitona', cat:'classicos', img:'https://i.pinimg.com/736x/e8/ed/20/e8ed20d0214d3033fdf86b708e2ac5fd.jpg'},
        
        // Monte o Seu Pastel
        {id:17, nome:'Monte seu Pastel (2 Recheios)', preco:17.50, cat:'monte', tipo:'monte', max:2, min:1, img:'https://i.pinimg.com/736x/01/4e/04/014e04188feecfd5ea2ac209eb3ad09b.jpg'},
        {id:18, nome:'Monte seu Pastel (3 Recheios)', preco:19.50, cat:'monte', tipo:'monte', max:3, min:2, img:'https://i.pinimg.com/736x/01/4e/04/014e04188feecfd5ea2ac209eb3ad09b.jpg'},
        {id:19, nome:'Monte seu Pastel (4 Recheios)', preco:21.50, cat:'monte', tipo:'monte', max:4, min:3, img:'https://i.pinimg.com/736x/01/4e/04/014e04188feecfd5ea2ac209eb3ad09b.jpg'},
        
        // Cuscuz
        {id:20, nome:'Cuscuz (2 Recheios)', preco:16.50, cat:'cuscuz', tipo:'monte', max:2, min:1, img:'https://i.pinimg.com/736x/b7/a1/a8/b7a1a8f4f27068bf9ab780cf38434bb0.jpg'},
        {id:21, nome:'Cuscuz (3 Recheios)', preco:18.50, cat:'cuscuz', tipo:'monte', max:3, min:2, img:'https://i.pinimg.com/736x/b7/a1/a8/b7a1a8f4f27068bf9ab780cf38434bb0.jpg'},
        {id:22, nome:'Cuscuz (4 Recheios)', preco:20.50, cat:'cuscuz', tipo:'monte', max:4, min:3, img:'https://i.pinimg.com/736x/b7/a1/a8/b7a1a8f4f27068bf9ab780cf38434bb0.jpg'},
        
        // Tapioca
        {id:23, nome:'Tapioca (2 Recheios)', preco:17.00, cat:'tapioca', tipo:'monte', max:2, min:1, img:'https://i.pinimg.com/736x/23/45/4a/23454a1e2d9d8885839c89a71cd90cbf.jpg'},
        {id:24, nome:'Tapioca (3 Recheios)', preco:19.00, cat:'tapioca', tipo:'monte', max:3, min:2, img:'https://i.pinimg.com/736x/23/45/4a/23454a1e2d9d8885839c89a71cd90cbf.jpg'},
        {id:25, nome:'Tapioca (4 Recheios)', preco:21.00, cat:'tapioca', tipo:'monte', max:4, min:3, img:'https://i.pinimg.com/736x/23/45/4a/23454a1e2d9d8885839c89a71cd90cbf.jpg'},
        
        // Porções
        {id:26, nome:'Batata Frita Ondulada P', preco:12.50, cat:'porcoes', img:'https://i.pinimg.com/736x/1e/b1/bb/1eb1bbf04ba24dbb9f0b1e8e8db2e719.jpg'},
        {id:27, nome:'Batata Frita Ondulada M', preco:16.50, cat:'porcoes', img:'https://i.pinimg.com/736x/1e/b1/bb/1eb1bbf04ba24dbb9f0b1e8e8db2e719.jpg'},
        {id:28, nome:'Batata Frita Palito P', preco:10.00, cat:'porcoes', img:'https://i.pinimg.com/736x/1e/b1/bb/1eb1bbf04ba24dbb9f0b1e8e8db2e719.jpg'},
        {id:29, nome:'Batata Frita Palito M', preco:14.00, cat:'porcoes', img:'https://i.pinimg.com/736x/1e/b1/bb/1eb1bbf04ba24dbb9f0b1e8e8db2e719.jpg'},
        {id:30, nome:'Bolinhas de Carne de Sol P (100g)', preco:12.00, cat:'porcoes', img:'https://i.pinimg.com/736x/1e/b1/bb/1eb1bbf04ba24dbb9f0b1e8e8db2e719.jpg'},
        {id:31, nome:'Bolinhas de Carne de Sol M (200g)', preco:21.00, cat:'porcoes', img:'https://i.pinimg.com/736x/1e/b1/bb/1eb1bbf04ba24dbb9f0b1e8e8db2e719.jpg'},
        {id:32, nome:'Mini Pastéis Pernambucanos (6 un)', preco:9.50, cat:'porcoes', img:'https://i.ytimg.com/vi/03C8mGqozSw/hq720.jpg'},
        
        // Bebidas
        {id:33, nome:'Batidinha de Uva Cremosa', preco:7.50, cat:'bebidas', tipo:'drink', img:'https://i.pinimg.com/736x/12/99/22/1299226e7417a8c5bcdaf7d21a0ac45e.jpg'},
        {id:34, nome:'Batidinha de Abacaxi Cremoso', preco:7.50, cat:'bebidas', tipo:'drink', img:'https://i.pinimg.com/736x/e2/96/29/e2962983d1f17481a303aa9d5a506f3c.jpg'},
        {id:35, nome:'Batidinha de Maracujá Cremoso', preco:9.50, cat:'bebidas', tipo:'drink', img:'https://i.pinimg.com/736x/42/82/a9/4282a913d5a689015ecc849a6a27029b.jpg'},
        {id:36, nome:'Batidinha de Morango Cremoso', preco:9.50, cat:'bebidas', tipo:'drink', img:'https://i.pinimg.com/736x/f5/35/5a/f5355aa77f9f84ce9c48cdad0901598d.jpg'},
        {id:37, nome:'Espanhola', preco:7.50, desc:'Uva, Abacaxi e Leite condensado', cat:'bebidas', tipo:'drink', img:'https://i.pinimg.com/736x/be/52/f9/be52f94c1721ef6e573bf97c56204c95.jpg'},
        {id:38, nome:'Morancujá', preco:9.50, desc:'Morango e Maracujá', cat:'bebidas', tipo:'drink', img:'https://i.pinimg.com/736x/52/07/e3/5207e32580c9e67594e2eabafd60631d.jpg'},
        {id:39, nome:'Morango com Abacaxi', preco:8.50, cat:'bebidas', tipo:'drink', img:'https://i.pinimg.com/736x/52/07/e3/5207e32580c9e67594e2eabafd60631d.jpg'},
        
        // Novidades
        {id:40, nome:'Mini Pastéis Pernambucanos', preco:16.50, desc:'6 unidades recheados com Carne, polvilhados com açúcar e canela', cat:'novidades', img:'https://i.ytimg.com/vi/03C8mGqozSw/hq720.jpg'}
    ];

    function filter(categoria) {
        // Atualizar botões ativos
        document.querySelectorAll('.cat-btn').forEach(btn => btn.classList.remove('active'));
        event.target.classList.add('active');
        
        // Filtrar produtos
        let produtosFiltrados = [];
        if (categoria === 'todos') {
            produtosFiltrados = db;
        } else {
            produtosFiltrados = db.filter(item => item.cat === categoria);
        }
        
        // Renderizar menu
        const menu = document.getElementById('menu');
        menu.innerHTML = produtosFiltrados.map(item => `
            <div class="card" onclick="clickProd(${item.id})">
                <div class="card-info">
                    <h3>${item.nome}</h3>
                    <p>${item.desc || ''}</p>
                    <span class="price">R$ ${item.preco.toFixed(2)}</span>
                </div>
                ${item.img ? `<img src="${item.img}" class="card-img">` : ''}
            </div>
        `).join('');
    }

    function clickProd(id) {
        const item = db.find(x => x.id === id);
        if (item.tipo === 'dueto') return openDueto(item);
        if (item.tipo === 'monte') return openMonte(item);
        if (item.tipo === 'drink') return openDrink(item);
        if (item.tipo === 'acai') return openAcai(item);
        addToCart(item.nome, item.preco);
    }

    function openDueto(item) {
        const modalBody = document.getElementById('custom-body');
        modalBody.innerHTML = `
            <h3>${item.nome}</h3>
            <img src="${item.img}" style="width:100%; max-height:200px; object-fit:cover; border-radius:10px; margin:10px 0">
            <p style="margin-bottom:15px">${item.desc}</p>
            
            <div style="margin:15px 0">
                <label><strong>1º Pastel:</strong></label>
                <select id="sabor1" style="width:100%; padding:10px; margin:5px 0 15px; border:1px solid #ddd; border-radius:8px">
                    <option>Carne</option>
                    <option>Frango</option>
                    <option>Mussarela</option>
                    <option>Coalho</option>
                </select>
                
                <label><strong>2º Pastel:</strong></label>
                <select id="sabor2" style="width:100%; padding:10px; margin:5px 0; border:1px solid #ddd; border-radius:8px">
                    <option>Carne</option>
                    <option>Frango</option>
                    <option>Mussarela</option>
                    <option>Coalho</option>
                </select>
            </div>
            
            <button class="btn-add" onclick="addDueto()">ADICIONAR À SACOLA</button>
        `;
        document.getElementById('modal-custom').style.display = 'flex';
    }

    function addDueto() {
        const s1 = document.getElementById('sabor1').value;
        const s2 = document.getElementById('sabor2').value;
        addToCart('Dueto Tradicional', 22.50, `Sabores: ${s1} e ${s2}`);
        closeAll();
    }

    function openAcai(item) {
        const modalBody = document.getElementById('custom-body');
        modalBody.innerHTML = `
            <h3>${item.nome}</h3>
            <img src="${item.img}" style="width:100%; max-height:200px; object-fit:cover; border-radius:10px; margin:10px 0">
            
            <div class="size-selector">
                <div class="size-btn" onclick="selectAcaiSize(300)">300ml</div>
                <div class="size-btn" onclick="selectAcaiSize(500)">500ml</div>
            </div>
            
            <div id="acaiOptions" style="margin-top:20px">
                ${generateAcaiOptions(300)}
            </div>
        `;
        document.getElementById('modal-custom').style.display = 'flex';
    }

    function selectAcaiSize(size) {
        document.querySelectorAll('.size-btn').forEach(btn => btn.classList.remove('selected'));
        event.target.classList.add('selected');
        document.getElementById('acaiOptions').innerHTML = generateAcaiOptions(size);
    }

    function generateAcaiOptions(size) {
        if (size === 300) {
            return `
                <div class="combo-grid">
                    <div class="combo-option" onclick="selectAcaiCombo(1, 300, 14.90)">1 un<br>R$ 14,90</div>
                    <div class="combo-option" onclick="selectAcaiCombo(2, 300, 26.00)">2 un<br>R$ 26,00</div>
                    <div class="combo-option" onclick="selectAcaiCombo(3, 300, 36.00)">3 un<br>R$ 36,00</div>
                </div>
                <button class="btn-add" onclick="addAcaiCombo()" id="addAcaiBtn" disabled>ADICIO
