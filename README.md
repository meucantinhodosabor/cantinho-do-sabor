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
        .opt-box { background: #f9f9f9; padding: 10px; border-radius: 8px; margin-bottom: 10px; cursor: pointer; border: 1px solid #eee; }
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
    <button class="cat-btn" onclick="filter('Açaí')">Açaí</button>
    <button class="cat-btn" onclick="filter('Clássicos')">Clássicos</button>
    <button class="cat-btn" onclick="filter('Monte o Seu')">Monte o Seu</button>
    <button class="cat-btn" onclick="filter('Cuscuz')">Cuscuz</button>
    <button class="cat-btn" onclick="filter('Tapioca')">Tapioca</button>
    <button class="cat-btn" onclick="filter('Porções')">Porções</button>
    <button class="cat-btn" onclick="filter('Bebidas')">Bebidas</button>
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
    const recheios = ["Frango", "Carne", "Pernil", "Salsicha", "Mussarela", "Coalho", "Milho", "Azeitona", "Cream Cheese", "Requeijão", "Cheddar", "Catupiry", "Alho Frito", "Pimenta"];

    const db = [
        {id:1, n:'Dueto Tradicional', p:22.50, d:'2 Pastéis (Carne, Frango, Mussarela ou Coalho)', cat:'Combos', type:'dueto'},
        {id:2, n:'Batidinha de Açaí 300ml', p:14.90, d:'Combos: 2un R$26 / 3un R$36', cat:'Açaí', type:'acai', vol:300},
        {id:3, n:'Batidinha de Açaí 500ml', p:22.00, d:'Combos: 2un R$39.90 / 3un R$57', cat:'Açaí', type:'acai', vol:500},
        {id:4, n:'Caipira Especial (Frango/Milho)', p:17.50, cat:'Clássicos', img:'https://i.pinimg.com/736x/54/f3/3e/54f33e374276eb01904b8a7bfe94081e.jpg'},
        {id:5, n:'O Queridinho (Carne/Queijo)', p:17.50, cat:'Clássicos', img:'https://i.pinimg.com/736x/0e/ba/e1/0ebae10f386aaf02dda228b58951ce41.jpg'},
        {id:6, n:'Pastel de Hotdog', p:17.50, cat:'Clássicos', img:'https://i.pinimg.com/736x/f6/ae/90/f6ae90345dc56319aa73d830743edb7f.jpg'},
        {id:7, n:'Frango Dourado', p:18.00, cat:'Clássicos', img:'https://i.pinimg.com/736x/90/7b/a5/907ba5cb7574a1ad9aa2eb0548c9eed4.jpg'},
        {id:8, n:'Sabor Mediterrâneo', p:18.00, cat:'Clássicos', img:'https://i.pinimg.com/736x/8f/f6/b2/8ff6b260aa8709cce002ec39f97a464c.jpg'},
        {id:9, n:'Super Cremoso', p:18.50, cat:'Clássicos', img:'https://i.pinimg.com/736x/66/20/80/662080576d5755f1fb79d243117a37d8.jpg'},
        {id:10, n:'Frango Clássico', p:18.50, cat:'Clássicos', img:'https://i.pinimg.com/736x/f4/29/44/f42944f3d798cf35a1e4fb028e62813a.jpg'},
        {id:11, n:'Cheddar Melt', p:18.50, cat:'Clássicos', img:'https://i.pinimg.com/736x/3b/ee/28/3bee28d4d4e562a48782b3c1371d4009.jpg'},
        {id:12, n:'Trio Imperial', p:18.50, cat:'Clássicos', img:'https://i.pinimg.com/736x/25/44/bb/2544bb486fc56f83130814b41c27b0a9.jpg'},
        {id:13, n:'Pernil Cremoso', p:19.50, cat:'Clássicos', img:'https://i.pinimg.com/736x/ee/65/0e/ee650e334bd5020ba51dfa1b32043d60.jpg'},
        {id:14, n:'Pernil Especial', p:20.00, cat:'Clássicos', img:'https://i.pinimg.com/736x/de/29/bf/de29bf0cfd6c1b1b2a52e37ea4e05c07.jpg'},
        {id:15, n:'Frango Gourmet', p:20.00, cat:'Clássicos', img:'https://i.pinimg.com/736x/fb/c8/f4/fbc8f415a71bfb628aed9f182affe245.jpg'},
        {id:16, n:'Carne Completa', p:20.00, cat:'Clássicos', img:'https://i.pinimg.com/736x/e8/ed/20/e8ed20d0214d3033fdf86b708e2ac5fd.jpg'},
        {id:17, n:'Monte seu Pastel (2 Rech)', p:17.50, cat:'Monte o Seu', type:'monte', max:2},
        {id:18, n:'Monte seu Pastel (3 Rech)', p:19.50, cat:'Monte o Seu', type:'monte', max:3},
        {id:19, n:'Monte seu Pastel (4 Rech)', p:21.50, cat:'Monte o Seu', type:'monte', max:4},
        {id:20, n:'Cuscuz (2 Rech)', p:16.50, cat:'Cuscuz', type:'monte', max:2},
        {id:21, n:'Cuscuz (3 Rech)', p:18.50, cat:'Cuscuz', type:'monte', max:3},
        {id:22, n:'Cuscuz (4 Rech)', p:20.50, cat:'Cuscuz', type:'monte', max:4},
        {id:23, n:'Tapioca (2 Rech)', p:17.00, cat:'Tapioca', type:'monte', max:2},
        {id:24, n:'Tapioca (3 Rech)', p:19.00, cat:'Tapioca', type:'monte', max:3},
        {id:25, n:'Tapioca (4 Rech)', p:21.00, cat:'Tapioca', type:'monte', max:4},
        {id:26, n:'Batata Ondulada P', p:12.50, cat:'Porções'},
        {id:27, n:'Batata Ondulada M', p:16.50, cat:'Porções'},
        {id:28, n:'Batata Palito P', p:10.00, cat:'Porções'},
        {id:29, n:'Batata Palito M', p:14.00, cat:'Porções'},
        {id:30, n:'Bolinhas Carne de Sol P', p:12.00, cat:'Porções', img:'https://i.pinimg.com/736x/1e/b1/bb/1eb1bbf04ba24dbb9f0b1e8e8db2e719.jpg'},
        {id:31, n:'Bolinhas Carne de Sol M', p:21.00, cat:'Porções', img:'https://i.pinimg.com/736x/1e/b1/bb/1eb1bbf04ba24dbb9f0b1e8e8db2e719.jpg'},
        {id:32, n:'Mini Pastéis (6 un)', p:9.50, cat:'Porções', img:'https://i.ytimg.com/vi/03C8mGqozSw/hq720.jpg'},
        {id:33, n:'Batidinha Uva', p:7.50, cat:'Bebidas', type:'drink'},
        {id:34, n:'Batidinha Abacaxi', p:7.50, cat:'Bebidas', type:'drink'},
        {id:35, n:'Batidinha Maracujá', p:9.50, cat:'Bebidas', type:'drink'},
        {id:36, n:'Batidinha Morango', p:9.50, cat:'Bebidas', type:'drink'},
        {id:37, n:'Espanhola', p:7.50, cat:'Bebidas', type:'drink'},
        {id:38, n:'Morancujá', p:9.50, cat:'Bebidas', type:'drink'},
        {id:39, n:'Morango c/ Abacaxi', p:8.50, cat:'Bebidas', type:'drink'},
        {id:40, n:'Mini Pernambucanos (6 un)', p:16.50, d:'Açúcar e canela', cat:'Novidades'}
    ];

    function filter(c) {
        document.querySelectorAll('.cat-btn').forEach(b => b.classList.remove('active'));
        event.target.classList.add('active');
        const list = c === 'Todos' ? db : db.filter(i => i.cat === c);
        document.getElementById('menu').innerHTML = list.map(i => `
            <div class="card" onclick="clickProd(${i.id})">
                <div class="card-info"><h3>${i.n}</h3><p>${i.d || ''}</p><span class="price">R$ ${i.p.toFixed(2)}</span></div>
                ${i.img ? `<img src="${i.img}" class="card-img">` : ''}
            </div>
        `).join('');
    }

    function clickProd(id) {
        const i = db.find(x => x.id === id);
        if(i.type === 'dueto') return openDueto(i);
        if(i.type === 'monte') return openMonte(i);
        if(i.type === 'drink') return openDrink(i);
        addCart(i.n, i.p);
    }

    function openDueto(i) {
        const b = document.getElementById('custom-body');
        b.innerHTML = `<h3>Escolha os 2 sabores</h3>
            <label>1º:</label><select id="s1"><option>Carne</option><option>Frango</option><option>Mussarela</option><option>Coalho</option></select><br><br>
            <label>2º:</label><select id="s2"><option>Carne</option><option>Frango</option><option>Mussarela</option><option>Coalho</option></select>
            <button class="btn-add" onclick="addCart('${i.n}', ${i.p}, 'Sabores: '+s1.value+', '+s2.value);closeAll()">ADICIONAR</button>`;
        document.getElementById('modal-custom').style.display = 'flex';
    }

    function openMonte(i) {
        const b = document.getElementById('custom-body');
        b.innerHTML = `<h3>Escolha até ${i.max} recheios</h3>
            <div style="display:grid;grid-template-columns:1fr 1fr;gap:5px;font-size:0.7rem;">
                ${recheios.map(r => `<label><input type="checkbox" class="rk" value="${r}"> ${r}</label>`).join('')}
            </div>
            <button class="btn-add" onclick="saveMonte('${i.n}', ${i.p}, ${i.max})">ADICIONAR</button>`;
        document.getElementById('modal-custom').style.display = 'flex';
    }

    function saveMonte(n, p, m) {
        const sel = Array.from(document.querySelectorAll('.rk:checked')).map(x => x.value);
        if(!sel.length || sel.length > m) return alert("Selecione de 1 a "+m);
        addCart(n, p, "Recheios: "+sel.join(", ")); closeAll();
    }

    function openDrink(i) {
        const b = document.getElementById('custom-body');
        b.innerHTML = `<h3>Tamanho:</h3>
            <div class="opt-box" onclick="addCart('${i.n} (300ml)', ${i.p});closeAll()">300ml - R$ ${i.p.toFixed(2)}</div>
            <div class="opt-box" onclick="addCart('${i.n} (500ml)', ${i.p+5});closeAll()">500ml - R$ ${(i.p+5).toFixed(2)}</div>`;
        document.getElementById('modal-custom').style.display = 'flex';
    }

    function addCart(n, p, d="") {
        const key = n+d;
        const x = cart.find(i => (i.n+i.d) === key);
        if(x) x.q++; else cart.push({n, p, q:1, d});
        updateUI();
    }

    function updateUI() {
        let t = 0, q = 0;
        cart.forEach(i => {
            q += i.q;
            if(i.n.includes('300ml') && i.n.includes('Açaí')) {
                if(i.q === 2) t += 26; else if(i.q >= 3) t += 36 + (i.q-3)*12; else t += i.p*i.q;
            } else if(i.n.includes('500ml') && i.n.includes('Açaí')) {
                if(i.q === 2) t += 39.9; else if(i.q >= 3) t += 57 + (i.q-3)*19; else t += i.p*i.q;
            } else t += i.p*i.q;
        });
        document.getElementById('cart-bar').style.display = q > 0 ? 'flex' : 'none';
        document.getElementById('c-qty').innerText = q;
        document.getElementById('c-total').innerText = 'R$ ' + t.toFixed(2);
        document.getElementById('f-total').innerText = 'R$ ' + t.toFixed(2);
    }

    function showCart() {
        document.getElementById('cart-list').innerHTML = cart.map((i, idx) => `
            <div style="display:flex;justify-content:space-between;font-size:0.8rem;margin-bottom:8px;">
                <span>${i.q}x ${i.n}<br><small>${i.d}</small></span>
                <div><button onclick="change(${idx},-1)">-</button> <button onclick="change(${idx},1)">+</button></div>
            </div>
        `).join('');
        document.getElementById('modal-cart').style.display = 'flex';
    }

    function change(idx, v) {
        cart[idx].q += v;
        if(cart[idx].q <= 0) cart.splice(idx,1);
        updateUI(); showCart();
        if(!cart.length) closeAll();
    }

    function checkPix() { document.getElementById('pix-info').style.display = document.getElementById('f-pay').value === 'Pix' ? 'block' : 'none'; }
    function closeAll() { document.querySelectorAll('.modal').forEach(m => m.style.display = 'none'); }

    document.getElementById('f-checkout').onsubmit = (e) => {
        e.preventDefault();
        const msg = `*PEDIDO CANTINHO DO SABOR*\nCliente: ${document.getElementById('f-nome').value}\nEndereço: ${document.getElementById('f-rua').value}\nReferência: ${document.getElementById('f-ref').value}\nPagamento: ${document.getElementById('f-pay').value}\n\n*ITENS:*\n` + cart.map(i => `${i.q}x ${i.n} ${i.d}`).join('\n') + `\n\n*TOTAL: ${document.getElementById('f-total').innerText}*`;
        window.open(`https://wa.me/${TEL}?text=${encodeURIComponent(msg)}`);
    };

    filter('Todos');
</script>
</body>
</html>
