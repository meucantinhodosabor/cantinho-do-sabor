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
    <button class="cat-btn active" onclick="filter('Todos')">Todos</button>
    <button class="cat-btn" onclick="filter('Combos')">Combos</button>
    <button class="cat-btn" onclick="filter('Açaí Gourmet')">Açaí Gourmet</button>
    <button class="cat-btn" onclick="filter('Clássicos')">Clássicos</button>
    <button class="cat-btn" onclick="filter('Monte o Seu')">Monte o Seu</button>
    <button class="cat-btn" onclick="filter('Cuscuz')">Cuscuz</button>
    <button class="cat-btn" onclick="filter('Tapioca')">Tapioca</button>
    <button class="cat-btn" onclick="filter('Novidades')">Novidades</button>
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
    let selectedCombo = null;
    let selectedRecheios = [];

    const recheios = [
        "Frango", "Carne", "Pernil", "Salsicha", "Mussarela", "Coalho", 
        "Milho", "Azeitona", "Cream Cheese", "Requeijão", "Cheddar", 
        "Catupiry", "Alho Frito", "Pimenta Calabresa"
    ];

    const db = [
        // Combos
        {id:1, n:'Dueto Tradicional', p:22.50, d:'2 Pastéis (Carne, Frango, Mussarela ou Coalho)', cat:'Combos', img:'https://i.pinimg.com/736x/c6/44/0a/c6440adee5ef7fa7d38f1e6e44f28be5.jpg', type:'dueto'},
        
        // Açaí Gourmet
        {id:2, n:'Batidinha de Açaí 300ml', p:14.90, cat:'Açaí Gourmet', type:'acai', img:'https://i.pinimg.com/736x/cf/3e/ce/cf3eced59ad15ee6fc1ffb3ebe057cd6.jpg'},
        {id:3, n:'Batidinha de Açaí 500ml', p:22.00, cat:'Açaí Gourmet', type:'acai', img:'https://i.pinimg.com/736x/cf/3e/ce/cf3eced59ad15ee6fc1ffb3ebe057cd6.jpg'},
        
        // Clássicos
        {id:4, n:'Caipira Especial', p:17.50, d:'Frango/Milho', cat:'Clássicos', img:'https://i.pinimg.com/736x/54/f3/3e/54f33e374276eb01904b8a7bfe94081e.jpg'},
        {id:5, n:'O Queridinho', p:17.50, d:'Carne/Queijo', cat:'Clássicos', img:'https://i.pinimg.com/736x/0e/ba/e1/0ebae10f386aaf02dda228b58951ce41.jpg'},
        {id:6, n:'Pastel de Hotdog', p:17.50, d:'Salsicha/Carne/Cheddar', cat:'Clássicos', img:'https://i.pinimg.com/736x/f6/ae/90/f6ae90345dc56319aa73d830743edb7f.jpg'},
        {id:7, n:'Frango Dourado', p:18.00, d:'Frango/Queijo', cat:'Clássicos', img:'https://i.pinimg.com/736x/90/7b/a5/907ba5cb7574a1ad9aa2eb0548c9eed4.jpg'},
        {id:8, n:'Sabor Mediterrâneo', p:18.00, d:'Carne/Azeitonas', cat:'Clássicos', img:'https://i.pinimg.com/736x/8f/f6/b2/8ff6b260aa8709cce002ec39f97a464c.jpg'},
        {id:9, n:'Super Cremoso', p:18.50, d:'Frango/Requeijão', cat:'Clássicos', img:'https://i.pinimg.com/736x/66/20/80/662080576d5755f1fb79d243117a37d8.jpg'},
        {id:10, n:'Frango Clássico', p:18.50, d:'Frango/Catupiry/Milho', cat:'Clássicos', img:'https://i.pinimg.com/736x/f4/29/44/f42944f3d798cf35a1e4fb028e62813a.jpg'},
        {id:11, n:'Cheddar Melt', p:18.50, d:'Carne/Cheddar', cat:'Clássicos', img:'https://i.pinimg.com/736x/3b/ee/28/3bee28d4d4e562a48782b3c1371d4009.jpg'},
        {id:12, n:'Trio Imperial', p:18.50, d:'3 Queijos', cat:'Clássicos', img:'https://i.pinimg.com/736x/25/44/bb/2544bb486fc56f83130814b41c27b0a9.jpg'},
        {id:13, n:'Pernil Cremoso', p:19.50, d:'Pernil/Catupiry/Milho', cat:'Clássicos', img:'https://i.pinimg.com/736x/ee/65/0e/ee650e334bd5020ba51dfa1b32043d60.jpg'},
        {id:14, n:'Pernil Especial', p:20.00, d:'Pernil/Coalho/Requeijão', cat:'Clássicos', img:'https://i.pinimg.com/736x/de/29/bf/de29bf0cfd6c1b1b2a52e37ea4e05c07.jpg'},
        {id:15, n:'Frango Gourmet', p:20.00, d:'Cream Cheese/Azeitona', cat:'Clássicos', img:'https://i.pinimg.com/736x/fb/c8/f4/fbc8f415a71bfb628aed9f182affe245.jpg'},
        {id:16, n:'Carne Completa', p:20.00, d:'Queijo/Milho/Azeitona', cat:'Clássicos', img:'https://i.pinimg.com/736x/e8/ed/20/e8ed20d0214d3033fdf86b708e2ac5fd.jpg'},
        
        // Monte o Seu Pastel
        {id:17, n:'Monte seu Pastel (2 Recheios)', p:17.50, cat:'Monte o Seu', type:'monte', max:2, min:1, img:'https://i.pinimg.com/736x/01/4e/04/014e04188feecfd5ea2ac209eb3ad09b.jpg'},
        {id:18, n:'Monte seu Pastel (3 Recheios)', p:19.50, cat:'Monte o Seu', type:'monte', max:3, min:2, img:'https://i.pinimg.com/736x/01/4e/04/014e04188feecfd5ea2ac209eb3ad09b.jpg'},
        {id:19, n:'Monte seu Pastel (4 Recheios)', p:21.50, cat:'Monte o Seu', type:'monte', max:4, min:3, img:'https://i.pinimg.com/736x/01/4e/04/014e04188feecfd5ea2ac209eb3ad09b.jpg'},
        
        // Cuscuz
        {id:20, n:'Cuscuz (2 Recheios)', p:16.50, cat:'Cuscuz', type:'monte', max:2, min:1, img:'https://i.pinimg.com/736x/b7/a1/a8/b7a1a8f4f27068bf9ab780cf38434bb0.jpg'},
        {id:21, n:'Cuscuz (3 Recheios)', p:18.50, cat:'Cuscuz', type:'monte', max:3, min:2, img:'https://i.pinimg.com/736x/b7/a1/a8/b7a1a8f4f27068bf9ab780cf38434bb0.jpg'},
        {id:22, n:'Cuscuz (4 Recheios)', p:20.50, cat:'Cuscuz', type:'monte', max:4, min:3, img:'https://i.pinimg.com/736x/b7/a1/a8/b7a1a8f4f27068bf9ab780cf38434bb0.jpg'},
        
        // Tapioca
        {id:23, n:'Tapioca (2 Recheios)', p:17.00, cat:'Tapioca', type:'monte', max:2, min:1, img:'https://i.pinimg.com/736x/23/45/4a/23454a1e2d9d8885839c89a71cd90cbf.jpg'},
        {id:24, n:'Tapioca (3 Recheios)', p:19.00, cat:'Tapioca', type:'monte', max:3, min:2, img:'https://i.pinimg.com/736x/23/45/4a/23454a1e2d9d8885839c89a71cd90cbf.jpg'},
        {id:25, n:'Tapioca (4 Recheios)', p:21.00, cat:'Tapioca', type:'monte', max:4, min:3, img:'https://i.pinimg.com/736x/23/45/4a/23454a1e2d9d8885839c89a71cd90cbf.jpg'},
        
        // Porções (acompanhamentos)
        {id:26, n:'Batata Frita Ondulada P', p:12.50, cat:'Porções', img:'https://i.pinimg.com/736x/1e/b1/bb/1eb1bbf04ba24dbb9f0b1e8e8db2e719.jpg'},
        {id:27, n:'Batata Frita Ondulada M', p:16.50, cat:'Porções', img:'https://i.pinimg.com/736x/1e/b1/bb/1eb1bbf04ba24dbb9f0b1e8e8db2e719.jpg'},
        {id:28, n:'Batata Frita Palito P', p:10.00, cat:'Porções', img:'https://i.pinimg.com/736x/1e/b1/bb/1eb1bbf04ba24dbb9f0b1e8e8db2e719.jpg'},
        {id:29, n:'Batata Frita Palito M', p:14.00, cat:'Porções', img:'https://i.pinimg.com/736x/1e/b1/bb/1eb1bbf04ba24dbb9f0b1e8e8db2e719.jpg'},
        {id:30, n:'Bolinhas de Carne de Sol P (100g)', p:12.00, cat:'Porções', img:'https://i.pinimg.com/736x/1e/b1/bb/1eb1bbf04ba24dbb9f0b1e8e8db2e719.jpg'},
        {id:31, n:'Bolinhas de Carne de Sol M (200g)', p:21.00, cat:'Porções', img:'https://i.pinimg.com/736x/1e/b1/bb/1eb1bbf04ba24dbb9f0b1e8e8db2e719.jpg'},
        {id:32, n:'Mini Pastéis Pernambucanos (6 un)', p:9.50, cat:'Porções', img:'https://i.ytimg.com/vi/03C8mGqozSw/hq720.jpg'},
        
        // Batidas e Drinks
        {id:33, n:'Batidinha de Uva Cremosa', p:7.50, cat:'Bebidas', type:'drink', img:'https://i.pinimg.com/736x/12/99/22/1299226e7417a8c5bcdaf7d21a0ac45e.jpg'},
        {id:34, n:'Batidinha de Abacaxi Cremoso', p:7.50, cat:'Bebidas', type:'drink', img:'https://i.pinimg.com/736x/e2/96/29/e2962983d1f17481a303aa9d5a506f3c.jpg'},
        {id:35, n:'Batidinha de Maracujá Cremoso', p:9.50, cat:'Bebidas', type:'drink', img:'https://i.pinimg.com/736x/42/82/a9/4282a913d5a689015ecc849a6a27029b.jpg'},
        {id:36, n:'Batidinha de Morango Cremoso', p:9.50, cat:'Bebidas', type:'drink', img:'https://i.pinimg.com/736x/f5/35/5a/f5355aa77f9f84ce9c48cdad0901598d.jpg'},
        {id:37, n:'Espanhola', p:7.50, d:'Uva, Abacaxi e Leite condensado', cat:'Bebidas', type:'drink', img:'https://i.pinimg.com/736x/be/52/f9/be52f94c1721ef6e573bf97c56204c95.jpg'},
        {id:38, n:'Morancujá', p:9.50, d:'Morango e Maracujá', cat:'Bebidas', type:'drink', img:'https://i.pinimg.com/736x/52/07/e3/5207e32580c9e67594e2eabafd60631d.jpg'},
        {id:39, n:'Morango com Abacaxi', p:8.50, cat:'Bebidas', type:'drink', img:'https://i.pinimg.com/736x/52/07/e3/5207e32580c9e67594e2eabafd60631d.jpg'},
        
        // Novidades
        {id:40, n:'Mini Pastéis Pernambucanos', p:16.50, d:'6 unidades recheados com Carne, polvilhados com açúcar e canela', cat:'Novidades', img:'https://i.ytimg.com/vi/03C8mGqozSw/hq720.jpg'}
    ];

    function filter(c) {
        document.querySelectorAll('.cat-btn').forEach(b => b.classList.remove('active'));
        event.target.classList.add('active');
        let list = [];
        if (c === 'Todos') {
            list = db;
        } else {
            list = db.filter(i => i.cat === c);
        }
        document.getElementById('menu').innerHTML = list.map(i => `
            <div class="card" onclick="clickProd(${i.id})">
                <div class="card-info">
                    <h3>${i.n}</h3>
                    <p>${i.d || ''}</p>
                    <span class="price">R$ ${i.p.toFixed(2)}</span>
                </div>
                ${i.img ? `<img src="${i.img}" class="card-img">` : ''}
            </div>
        `).join('');
    }

    function clickProd(id) {
        const i = db.find(x => x.id === id);
        if(i.type === 'dueto') return openDueto(i);
        if(i.type === 'monte') return openMonte(i);
        if(i.type === 'drink') return openDrink(i);
        if(i.type === 'acai') return openAcai(i);
        addToCart(i.n, i.p);
    }

    function openDueto(i) {
        const b = document.getElementById('custom-body');
        b.innerHTML = `
            <h3>Escolha os 2 sabores</h3>
            <div style="margin:15px 0">
                <label><strong>1º Pastel:</strong></label>
                <select id="s1" class="form-group" style="width:100%; padding:10px; margin:5px 0 15px">
                    <option>Carne</option>
                    <option>Frango</option>
                    <option>Mussarela</option>
                    <option>Coalho</option>
                </select>
                
                <label><strong>2º Pastel:</strong></label>
                <select id="s2" class="form-group" style="width:100%; padding:10px; margin:5px 0">
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
        const s1 = document.getElementById('s1').value;
        const s2 = document.getElementById('s2').value;
        const item = db.find(x => x.id === 1);
        addToCart(item.n, item.p, `Sabores: ${s1} e ${s2}`);
        closeAll();
    }

    function openAcai(i) {
        const b = document.getElementById('custom-body');
        b.innerHTML = `
            <h3>Batidinha de Açaí Gourmet</h3>
            <img src="${i.img}" style="width:100%; max-height:200px; object-fit:cover; border-radius:10px; margin:10px 0">
            
            <div class="size-selector">
                <div class="size-btn ${i.n.includes('300ml') ? 'selected' : ''}" onclick="selectAcaiSize(300)">300ml</div>
                <div class="size-btn ${i.n.includes('500ml') ? 'selected' : ''}" onclick="selectAcaiSize(500)">500ml</div>
            </div>
            
            <div id="acai-options">
                ${generateAcaiOptions(i.n.includes('300ml') ? 300 : 500)}
            </div>
        `;
        selectedSize = i.n.includes('300ml') ? 300 : 500;
        document.getElementById('modal-custom').style.display = 'flex';
    }

    function selectAcaiSize(size) {
        document.querySelectorAll('.size-btn').forEach(btn => btn.classList.remove('selected'));
        event.target.classList.add('selected');
        selectedSize = size;
        document.getElementById('acai-options').innerHTML = generateAcaiOptions(size);
    }

    function generateAcaiOptions(size) {
        if (size === 300) {
            return `
                <div class="combo-grid">
                    <div class="combo-option" onclick="selectAcaiCombo(1, 300)">1 un<br>R$ 14,90</div>
                    <div class="combo-option" onclick="selectAcaiCombo(2, 300)">2 un<br>R$ 26,00</div>
                    <div class="combo-option" onclick="selectAcaiCombo(3, 300)">3 un<br>R$ 36,00</div>
                </div>
                <button class="btn-add" onclick="addAcaiCombo()">ADICIONAR À SACOLA</button>
            `;
        } else {
            return `
                <div class="combo-grid">
                    <div class="combo-option" onclick="selectAcaiCombo(1, 500)">1 un<br>R$ 22,00</div>
                    <div class="combo-option" onclick="selectAcaiCombo(2, 500)">2 un<br>R$ 39,90</div>
                    <div class="combo-option" onclick="selectAcaiCombo(3, 500)">3 un<br>R$ 57,00</div>
                </div>
                <button class="btn-add" onclick="addAcaiCombo()">ADICIONAR À SACOLA</button>
            `;
        }
    }

    function selectAcaiCombo(qty, size) {
        document.querySelectorAll('.combo-option').forEach(btn => btn.classList.remove('selected'));
        event.target.classList.add('selected');
        selectedCombo = {qty, size};
    }

    function addAcaiCombo() {
        if (!selectedCombo) return alert('Selecione uma opção');
        const {qty, size} = selectedCombo;
        let price = 0;
        if (size === 300) {
            if (qty === 1) price = 14.90;
            else if (qty === 2) price = 26.00;
            else price = 36.00;
        } else {
            if (qty === 1) price = 22.00;
            else if (qty === 2) price = 39.90;
            else price = 57.00;
        }
        addToCart(`Açaí ${size}ml (${qty} un)`, price);
        closeAll();
    }

    function openMonte(i) {
        const b = document.getElementById('custom-body');
        selectedRecheios = [];
        currentItem = i;
        
        b.innerHTML = `
            <h3>${i.n}</h3>
            <img src="${i.img}" style="width:100%; max-height:200px; object-fit:cover; border-radius:10px; margin:10px 0">
            <p style="color:#666; margin-bottom:10px">Selecione de ${i.min} a ${i.max} recheios</p>
            
            <div class="recheios-grid" id="recheios-list">
                ${recheios.map(r => `
                    <label class="recheio-item">
                        <input type="checkbox" value="${r}" onchange="updateRecheios(this, ${i.min}, ${i.max})"> ${r}
                    </label>
                `).join('')}
            </div>
            
            <div style="margin:15px 0">
                <h4>Acompanhamentos (opcional)</h4>
                ${generateAccompaniments()}
            </div>
            
            <div style="margin:15px 0">
                <h4>Bebidas (opcional)</h4>
                ${generateDrinks()}
            </div>
            
            <button class="btn-add" id="addMonteBtn" onclick="addMonte()" disabled>ADICIONAR À SACOLA</button>
        `;
        document.getElementById('modal-custom').style.display = 'flex';
    }

    function generateAccompaniments() {
        const items = db.filter(x => x.cat === 'Porções');
        return items.map(item => `
            <div style="display:flex; justify-content:space-between; align-items:center; margin:5px 0; padding:5px; background:#f9f9f9; border-radius:5px">
                <span>${item.n} - R$ ${item.p.toFixed(2)}</span>
                <button onclick="addExtra('${item.n}', ${item.p})" style="background:#ff4500; color:white; border:none; padding:5px 10px; border-radius:5px; cursor:pointer">+</button>
            </div>
        `).join('');
    }

    function generateDrinks() {
        const items = db.filter(x => x.cat === 'Bebidas');
        return items.map(item => `
            <div style="display:flex; justify-content:space-between; align-items:center; margin:5px 0; padding:5px; background:#f9f9f9; border-radius:5px">
                <span>${item.n} - R$ ${item.p.toFixed(2)}</span>
                <button onclick="openDrinkExtra('${item.n}', ${item.p})" style="background:#ff4500; color:white; border:none; padding:5px 10px; border-radius:5px; cursor:pointer">+</button>
            </div>
        `).join('');
    }

    function openDrinkExtra(name, basePrice) {
        const b = document.getElementById('custom-body');
        b.innerHTML = `
            <h3>${name}</h3>
            <p>Escolha o tamanho:</p>
            <div class="size-selector" style="margin:15px 0">
                <div class="size-btn" onclick="selectDrinkSize(300, ${basePrice})">300ml - R$ ${basePrice.toFixed(2)}</div>
                <div class="size-btn" onclick="selectDrinkSize(500, ${basePrice + 5})">500ml - R$ ${(basePrice + 5).toFixed(2)}</div>
            </div>
            <button class="btn-add" onclick="addDrinkExtra('${name}')" id="drinkAddBtn" disabled>ADICIONAR</button>
        `;
        selectedSize = null;
        document.getElementById('modal-custom').style.display = 'flex';
    }

    function selectDrinkSize(size, price) {
        document.querySelectorAll('.size-btn').forEach(btn => btn.classList.remove('selected'));
        event.target.classList.add('selected');
        selectedSize = size;
        selectedPrice = price;
        document.getElementById('drinkAddBtn').disabled = false;
    }

    function addDrinkExtra(name) {
        if (!selectedSize) return alert('Selecione um tamanho');
        addToCart(`${name} (${selectedSize}ml)`, selectedPrice);
        openMonte(currentItem);
    }

    function addExtra(name, price) {
        addToCart(name, price);
    }

    function updateRecheios(checkbox, min, max) {
        if (checkbox.checked) {
            selectedRecheios.push(checkbox.value);
        } else {
            selectedRecheios = selectedRecheios.filter(r => r !== checkbox.value);
        }
        
        // Desabilitar checkboxes se atingir o máximo
        if (selectedRecheios.length >= max) {
            document.querySelectorAll('.recheio-item input:not(:checked)').forEach(cb => {
                cb.disabled = true;
            });
        } else {
            document.querySelectorAll('.recheio-item input').forEach(cb => {
                cb.disabled = false;
            });
        }
        
        // Habilitar botão se atingir o mínimo
        const addBtn = document.getElementById('addMonteBtn');
        if (selectedRecheios.length >= min && selectedRecheios.length <= max) {
            addBtn.disabled = false;
        } else {
            addBtn.disabled = true;
        }
    }

    function addMonte() {
        if (!currentItem) return;
        addToCart(currentItem.n, currentItem.p, `Recheios: ${selectedRecheios.join(', ')}`);
        closeAll();
    }

    function openDrink(i) {
        const b = document.getElementById('custom-body');
        b.innerHTML = `
            <h3>${i.n}</h3>
            <img src="${i.img}" style="width:100%; max-height:200px; object-fit:cover; border-radius:10px; margin:10px 0">
            <p>Escolha o tamanho:</p>
            <div class="size-selector" style="margin:15px 0">
                <div class="size-btn" onclick="selectDrinkSize(300, ${i.p})">300ml - R$ ${i.p.toFixed(2)}</div>
                <div class="size-btn" onclick="selectDrinkSize(500, ${i.p + 5})">500ml - R$ ${(i.p + 5).toFixed(2)}</div>
            </div>
            <button class="btn-add" onclick="addDrink()" id="drinkAddBtn" disabled>ADICIONAR À SACOLA</button>
        `;
        currentItem = i;
        selectedSize = null;
        document.getElementById('modal-custom').style.display = 'flex';
    }

    function addDrink() {
        if (!selectedSize) return alert('Selecione um tamanho');
        addToCart(`${currentItem.n} (${selectedSize}ml)`, selectedPrice);
        closeAll();
    }

    function addToCart(name, price, details = "") {
        const key = name + details;
        const existing = cart.find(item => (item.name + item.details) === key);
        
        if (existing) {
            existing.qty++;
        } else {
            cart.push({ name, price, qty: 1, details });
        }
        
        updateUI();
    }

    function updateUI() {
        let total = 0;
        let qty = 0;
        
        cart.forEach(item => {
            qty += item.qty;
            total += item.price * item.qty;
        });
        
        document.getElementById('cart-bar').style.display = qty > 0 ? 'flex' : 'none';
        document.getElementById('c-qty').innerText = qty;
        document.getElementById('c-total').innerText = 'R$ ' + total.toFixed(2);
        document.getElementById('f-total').innerText = 'R$ ' + total.toFixed(2);
    }

    function showCart() {
        const cartList = document.getElementById('cart-list');
        cartList.innerHTML = cart.map((item, index) => `
            <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:10px; padding:10px; background:#f9f9f9; border-radius:8px">
                <div>
                    <strong>${item.qty}x ${item.name}</strong>
                    ${item.details ? `<br><small style="color:#666">${item.details}</small>` : ''}
                </div>
                <div style="display:flex; align-items:center; gap:10px">
                    <span>R$ ${(item.price * item.qty).toFixed(2)}</span>
                    <div>
                        <button onclick="changeQty(${index}, -1)" style="background:#ff4500; color:white; border:none; width:30px; height:30px; border-radius:5px; cursor:pointer">-</button>
                        <button onclick="changeQty(${index}, 1)" style="background:#ff4500; color:white; border:none; width:30px; height:30px; border-radius:5px; cursor:pointer">+</button>
                    </div>
                </div>
            </div>
        `).join('');
        
        document.getElementById('modal-cart').style.display = 'flex';
    }

    function changeQty(index, delta) {
        cart[index].qty += delta;
        if (cart[index].qty <= 0) {
            cart.splice(index, 1);
        }
        updateUI();
        showCart();
    }

    function checkPix() {
        const paySelect = document.getElementById('f-pay');
        const pixInfo = document.getElementById('pix-info');
        pixInfo.style.display = paySelect.value === 'Pix' ? 'block' : 'none';
    }

    function closeAll() {
        document.querySelectorAll('.modal').forEach(m => m.style.display = 'none');
    }

    document.getElementById('f-checkout').onsubmit = (e) => {
        e.preventDefault();
        
        const nome = document.getElementById('f-nome').value;
        const endereco = document.getElementById('f-rua').value;
        const ref = document.getElementById('f-ref').value;
        const pagamento = document.getElementById('f-pay').value;
        const total = document.getElementById('f-total').innerText;
        
        let itemsText = '';
        cart.forEach(item => {
            itemsText += `${item.qty}x ${item.name} ${item.details ? '- ' + item.details : ''}\n`;
        });
        
        const message = `*CANTINHO DO SABOR - NOVO PEDIDO*\n\n` +
            `*Cliente:* ${nome}\n` +
            `*Endereço:* ${endereco}\n` +
            `*Referência:* ${ref}\n` +
            `*Pagamento:* ${pagamento}\n\n` +
            `*ITENS:*\n${itemsText}\n` +
            `*TOTAL:* ${total}`;
        
        window.open(`https://wa.me/${TEL}?text=${encodeURIComponent(message)}`);
    };

    // Inicializar com todos os itens
    filter('Todos');
</script>
</body>
</html>
