<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
  <title>Cantinho do Sabor • delivery</title>
  <style>
    /* ===== RESET & FONT ===== */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    }

    :root {
      --white: #ffffff;
      --gray-light: #f5f5f5;
      --gray-medium: #e0e0e0;
      --gray-dark: #2e2e2e;
      --black: #121212;
      --orange-start: #ff7a00;
      --orange-end: #ff3d00;
      --shadow-sm: 0 4px 12px rgba(0, 0, 0, 0.04);
      --shadow-md: 0 8px 24px rgba(0, 0, 0, 0.08);
      --radius-card: 16px;
      --radius-full: 9999px;
    }

    body {
      background-color: var(--gray-light);
      color: var(--black);
      line-height: 1.4;
      padding-bottom: 90px; /* espaço para o carrinho fixo */
    }

    /* ===== TYPOGRAPHY & UTILS ===== */
    h1, h2, h3 {
      font-weight: 600;
      letter-spacing: -0.02em;
    }

    .price {
      font-weight: 700;
      color: var(--orange-end);
    }

    /* ===== HEADER HERO ===== */
    .hero {
      width: 100%;
      height: 200px;
      background: url('https://i.pinimg.com/736x/15/ac/c8/15acc8b00600f7f49f899cccbb55050d.jpg') center/cover;
      position: relative;
      border-bottom-left-radius: var(--radius-card);
      border-bottom-right-radius: var(--radius-card);
    }

    .hero::after {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(to bottom, transparent 60%, rgba(0,0,0,0.2));
      border-radius: inherit;
    }

    .logo-wrapper {
      position: absolute;
      bottom: -48px;
      left: 50%;
      transform: translateX(-50%);
      width: 96px;
      height: 96px;
      border-radius: var(--radius-full);
      border: 4px solid var(--white);
      box-shadow: var(--shadow-md);
      background: white;
      z-index: 5;
    }

    .logo-wrapper img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      border-radius: inherit;
    }

    .store-info {
      margin-top: 56px;
      text-align: center;
      padding: 12px 16px;
      background: var(--white);
      border-radius: var(--radius-card);
      box-shadow: var(--shadow-sm);
      width: calc(100% - 32px);
      margin-left: auto;
      margin-right: auto;
    }

    .store-info h1 {
      font-size: 1.8rem;
      background: linear-gradient(135deg, var(--orange-start), var(--orange-end));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      margin-bottom: 4px;
    }

    .store-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      justify-content: center;
      font-size: 0.9rem;
      color: var(--gray-dark);
    }

    .store-tags span {
      background: var(--gray-light);
      padding: 6px 14px;
      border-radius: 40px;
      display: inline-flex;
      align-items: center;
      gap: 4px;
    }

    /* ===== CARDÁPIO ===== */
    .container {
      max-width: 560px;
      margin: 0 auto;
      padding: 16px;
    }

    .category {
      margin-bottom: 32px;
    }

    .category h2 {
      font-size: 1.5rem;
      margin-bottom: 12px;
      padding-left: 8px;
      border-left: 5px solid var(--orange-start);
    }

    .product-grid {
      display: flex;
      flex-direction: column;
      gap: 16px;
    }

    .product-card {
      background: var(--white);
      border-radius: var(--radius-card);
      padding: 12px;
      display: flex;
      gap: 12px;
      box-shadow: var(--shadow-sm);
      transition: all 0.2s ease;
      border: 1px solid transparent;
    }

    .product-card:active {
      transform: scale(0.99);
      border-color: var(--orange-start);
    }

    .product-img {
      width: 80px;
      height: 80px;
      border-radius: 12px;
      object-fit: cover;
      background: var(--gray-medium);
      flex-shrink: 0;
    }

    .product-info {
      flex: 1;
    }

    .product-info h3 {
      font-size: 1.1rem;
      margin-bottom: 4px;
    }

    .product-desc {
      font-size: 0.85rem;
      color: #555;
      margin-bottom: 8px;
    }

    .product-footer {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .add-btn {
      background: linear-gradient(135deg, var(--orange-start), var(--orange-end));
      border: none;
      color: white;
      font-weight: 600;
      padding: 8px 16px;
      border-radius: 40px;
      font-size: 0.9rem;
      cursor: pointer;
      box-shadow: 0 4px 8px rgba(255, 61, 0, 0.2);
      transition: opacity 0.2s;
    }

    .add-btn:active {
      opacity: 0.7;
    }

    /* extras pequenos */
    .extras-group {
      background: var(--white);
      border-radius: var(--radius-card);
      padding: 16px;
      margin: 16px 0;
    }
    .extra-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 8px 0;
      border-bottom: 1px dashed var(--gray-medium);
    }

    /* ===== DRAWER CARRINHO (SACOLA) ===== */
    .cart-drawer {
      position: fixed;
      bottom: 0;
      left: 0;
      width: 100%;
      background: var(--white);
      border-top-left-radius: 24px;
      border-top-right-radius: 24px;
      box-shadow: 0 -8px 30px rgba(0,0,0,0.12);
      z-index: 1000;
      transition: transform 0.3s ease;
      max-height: 80vh;
      display: flex;
      flex-direction: column;
    }

    .cart-drawer.collapsed {
      transform: translateY(calc(100% - 72px));
    }

    .cart-handle {
      padding: 16px;
      text-align: center;
      font-weight: 600;
      background: var(--white);
      border-top-left-radius: 24px;
      border-top-right-radius: 24px;
      cursor: pointer;
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 1px solid var(--gray-medium);
    }

    .cart-items-container {
      overflow-y: auto;
      padding: 16px;
      flex: 1;
    }

    .cart-item {
      display: flex;
      gap: 8px;
      align-items: center;
      padding: 8px 0;
      border-bottom: 1px solid var(--gray-light);
    }
    .cart-item-info { flex:1; }
    .cart-item-actions { display: flex; align-items: center; gap: 8px; }
    .cart-item-actions button {
      background: var(--gray-light);
      border: none;
      width: 30px; height: 30px;
      border-radius: 30px;
      font-weight: bold;
      font-size: 1.2rem;
    }
    .cart-total {
      padding: 16px;
      background: var(--gray-light);
      font-weight: 700;
    }
    .checkout-btn {
      background: linear-gradient(135deg, var(--orange-start), var(--orange-end));
      color: white;
      border: none;
      padding: 16px;
      font-size: 1.2rem;
      font-weight: 700;
      width: 100%;
      border-radius: 40px;
      margin-top: 8px;
      cursor: pointer;
    }
    .checkout-btn:disabled {
      opacity: 0.4;
      pointer-events: none;
    }

    /* ===== MODAL PIX ===== */
    .modal-pix {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: rgba(0,0,0,0.5);
      display: none;
      align-items: center;
      justify-content: center;
      z-index: 2000;
    }
    .modal-content {
      background: white;
      width: 90%;
      max-width: 360px;
      border-radius: 32px;
      padding: 24px;
      text-align: center;
    }
    .pix-code {
      background: var(--gray-light);
      padding: 12px;
      border-radius: 12px;
      font-family: monospace;
      word-break: break-all;
      margin: 16px 0;
    }
    .copy-btn {
      background: var(--black);
      color: white;
      border: none;
      padding: 12px 24px;
      border-radius: 40px;
      font-weight: 600;
    }

    /* ===== FORM ===== */
    .checkout-form {
      background: white;
      border-radius: var(--radius-card);
      padding: 16px;
      margin-top: 16px;
    }
    .form-group {
      margin-bottom: 12px;
    }
    .form-group input, select {
      width: 100%;
      padding: 14px;
      border: 1px solid var(--gray-medium);
      border-radius: 40px;
      font-size: 1rem;
    }
    .payment-options {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin: 8px 0;
    }
    .payment-options label {
      background: var(--gray-light);
      padding: 8px 16px;
      border-radius: 40px;
      display: flex;
      align-items: center;
      gap: 4px;
    }

    /* ===== MICRO ANIMAÇÕES ===== */
    .toast-feedback {
      position: fixed;
      bottom: 100px; left: 50%; transform: translateX(-50%);
      background: var(--black);
      color: white;
      padding: 8px 20px;
      border-radius: 40px;
      font-size: 0.9rem;
      opacity: 0;
      transition: opacity 0.2s;
      z-index: 3000;
    }
  </style>
</head>
<body>
  <!-- HERO -->
  <div class="hero">
    <div class="logo-wrapper">
      <img src="https://i.pinimg.com/736x/15/ac/c8/15acc8b00600f7f49f899cccbb55050d.jpg" alt="Cantinho do Sabor">
    </div>
  </div>
  <div class="store-info">
    <h1>Cantinho do Sabor</h1>
    <div class="store-tags">
      <span>🍟 Entrega grátis</span>
      <span>⏱️ 40–50 min</span>
      <span>⭐ 4.9</span>
    </div>
  </div>

  <main class="container" id="cardapio"></main>

  <!-- CARRINHO DRAWER -->
  <div class="cart-drawer collapsed" id="cartDrawer">
    <div class="cart-handle" id="cartHandle">
      <span>🛒 Sacola <span id="itemCount">0</span></span>
      <span id="drawerToggle">▲</span>
    </div>
    <div class="cart-items-container" id="cartItems"></div>
    <div class="cart-total">
      <div>Subtotal: R$ <span id="subtotal">0.00</span></div>
      <div>Total: R$ <span id="total">0.00</span></div>
      <button class="checkout-btn" id="checkoutBtn" disabled>Finalizar pedido</button>
    </div>
  </div>

  <!-- MODAL PIX -->
  <div class="modal-pix" id="pixModal">
    <div class="modal-content">
      <h3>Pagamento PIX</h3>
      <div class="pix-code" id="pixCodeText">82e5f2e0-772e-46d6-8ec9-3dbcf9b2c54c</div>
      <button class="copy-btn" id="copyPixBtn">Copiar código</button>
      <p style="margin-top:12px">Após copiar, finalize no WhatsApp</p>
    </div>
  </div>

  <div class="toast-feedback" id="toast">Código copiado!</div>

  <script>
    (function() {
      // ---------- DADOS COMPLETOS DO CARDÁPIO ----------
      const produtos = [];

      // 1. Combos Promocionais
      produtos.push({
        id: 'dueto',
        nome: 'Dueto Tradicional',
        descricao: '2 Pastéis de 1 recheio (Carne, Mussarela, Coalho ou Frango)',
        preco: 22.50,
        img: 'https://i.pinimg.com/736x/c6/44/0a/c6440adee5ef7fa7d38f1e6e44f28be5.jpg',
        categoria: '🔥 Combos Promocionais',
        tipo: 'dueto',
        recheios: ['Carne', 'Mussarela', 'Coalho', 'Frango'],
        maxRecheios: 2,
        obrigatorioRecheio: true
      });

      // 2. Batidinhas Açaí Gourmet
      const acai300 = [14.90, 26.00, 36.00];
      const acai500 = [22.00, 39.90, 57.00];
      ['300ml', '500ml'].forEach((size, idxSize) => {
        const prices = idxSize === 0 ? acai300 : acai500;
        ['1 Unidade', 'Combo 2', 'Combo 3'].forEach((nome, i) => {
          produtos.push({
            id: `acai-${size}-${i}`,
            nome: `Açaí ${size} - ${nome}`,
            descricao: `Batidinha de Açaí Gourmet ${size}`,
            preco: prices[i],
            img: 'https://i.pinimg.com/736x/cf/3e/ce/cf3eced59ad15ee6fc1ffb3ebe057cd6.jpg',
            categoria: '🥣 Batidinhas de Açaí Gourmet'
          });
        });
      });

      // 3. Clássicos Inesquecíveis (lista longa)
      const classicos = [
        { nome: 'Caipira Especial (Frango/Milho)', preco: 17.50, img: 'https://i.pinimg.com/736x/54/f3/3e/54f33e374276eb01904b8a7bfe94081e.jpg' },
        { nome: 'O Queridinho (Carne/Queijo)', preco: 17.50, img: 'https://i.pinimg.com/736x/0e/ba/e1/0ebae10f386aaf02dda228b58951ce41.jpg' },
        { nome: 'Pastel de Hotdog (Salsicha/Carne/Cheddar)', preco: 17.50, img: 'https://i.pinimg.com/736x/f6/ae/90/f6ae90345dc56319aa73d830743edb7f.jpg' },
        { nome: 'Frango Dourado (Frango/Queijo)', preco: 18.00, img: 'https://i.pinimg.com/736x/90/7b/a5/907ba5cb7574a1ad9aa2eb0548c9eed4.jpg' },
        { nome: 'Sabor Mediterrâneo (Carne/Azeitonas)', preco: 18.00, img: 'https://i.pinimg.com/736x/8f/f6/b2/8ff6b260aa8709cce002ec39f97a464c.jpg' },
        { nome: 'Super Cremoso (Frango/Requeijão)', preco: 18.50, img: 'https://i.pinimg.com/736x/66/20/80/662080576d5755f1fb79d243117a37d8.jpg' },
        { nome: 'Frango Clássico (Frango/Catupiry/Milho)', preco: 18.50, img: 'https://i.pinimg.com/736x/f4/29/44/f42944f3d798cf35a1e4fb028e62813a.jpg' },
        { nome: 'Cheddar Melt (Carne/Cheddar)', preco: 18.50, img: 'https://i.pinimg.com/736x/3b/ee/28/3bee28d4d4e562a48782b3c1371d4009.jpg' },
        { nome: 'Trio Imperial (3 Queijos)', preco: 18.50, img: 'https://i.pinimg.com/736x/25/44/bb/2544bb486fc56f83130814b41c27b0a9.jpg' },
        { nome: 'Pernil Cremoso (Pernil/Catupiry/Milho)', preco: 19.50, img: 'https://i.pinimg.com/736x/ee/65/0e/ee650e334bd5020ba51dfa1b32043d60.jpg' },
        { nome: 'Pernil Especial (Pernil/Coalho/Requeijão)', preco: 20.00, img: 'https://i.pinimg.com/736x/de/29/bf/de29bf0cfd6c1b1b2a52e37ea4e05c07.jpg' },
        { nome: 'Frango Gourmet (Cream Cheese/Azeitona)', preco: 20.00, img: 'https://i.pinimg.com/736x/fb/c8/f4/fbc8f415a71bfb628aed9f182affe245.jpg' },
        { nome: 'Carne Completa (Queijo/Milho/Azeitona)', preco: 20.00, img: 'https://i.pinimg.com/736x/e8/ed/20/e8ed20d0214d3033fdf86b708e2ac5fd.jpg' }
      ];
      classicos.forEach((c, idx) => produtos.push({ ...c, id: `classico-${idx}`, categoria: '🥟 Clássicos Inesquecíveis' }));

      // 4. Monte o seu Pastel Crocante (com recheios)
      const recheiosDisponiveis = ['Frango','Carne','Pernil','Salsicha','Mussarela','Coalho','Milho','Azeitona','Cream Cheese','Requeijão','Cheddar','Catupiry','Alho Frito','Pimenta Calabresa'];
      produtos.push({ id: 'pastel2', nome: 'Pastel 2 Recheios', preco: 17.50, img: 'https://i.pinimg.com/736x/01/4e/04/014e04188feecfd5ea2ac209eb3ad09b.jpg', categoria: '🛠 Monte o Seu Pastel', tipo: 'montar', maxRecheios:2, minRecheios:1, recheios: recheiosDisponiveis });
      produtos.push({ id: 'pastel3', nome: 'Pastel 3 Recheios', preco: 19.50, img: 'https://i.pinimg.com/736x/01/4e/04/014e04188feecfd5ea2ac209eb3ad09b.jpg', categoria: '🛠 Monte o Seu Pastel', tipo: 'montar', maxRecheios:3, minRecheios:2, recheios: recheiosDisponiveis });
      produtos.push({ id: 'pastel4', nome: 'Pastel 4 Recheios', preco: 21.50, img: 'https://i.pinimg.com/736x/01/4e/04/014e04188feecfd5ea2ac209eb3ad09b.jpg', categoria: '🛠 Monte o Seu Pastel', tipo: 'montar', maxRecheios:4, minRecheios:3, recheios: recheiosDisponiveis });

      // 5. Cuscuz recheado
      produtos.push({ id: 'cuscuz2', nome: 'Cuscuz 2 Recheios', preco: 16.50, img: 'https://i.pinimg.com/736x/b7/a1/a8/b7a1a8f4f27068bf9ab780cf38434bb0.jpg', categoria: '🌽 Monte o Seu Cuscuz', tipo: 'montar', maxRecheios:2, minRecheios:1, recheios: recheiosDisponiveis });
      produtos.push({ id: 'cuscuz3', nome: 'Cuscuz 3 Recheios', preco: 18.50, img: 'https://i.pinimg.com/736x/b7/a1/a8/b7a1a8f4f27068bf9ab780cf38434bb0.jpg', categoria: '🌽 Monte o Seu Cuscuz', tipo: 'montar', maxRecheios:3, minRecheios:2, recheios: recheiosDisponiveis });
      produtos.push({ id: 'cuscuz4', nome: 'Cuscuz 4 Recheios', preco: 20.50, img: 'https://i.pinimg.com/736x/b7/a1/a8/b7a1a8f4f27068bf9ab780cf38434bb0.jpg', categoria: '🌽 Monte o Seu Cuscuz', tipo: 'montar', maxRecheios:4, minRecheios:3, recheios: recheiosDisponiveis });

      // 6. Tapioca recheada
      produtos.push({ id: 'tapioca2', nome: 'Tapioca 2 Recheios', preco: 17.00, img: 'https://i.pinimg.com/736x/23/45/4a/23454a1e2d9d8885839c89a71cd90cbf.jpg', categoria: '🫔 Monte a Sua Tapioca', tipo: 'montar', maxRecheios:2, minRecheios:1, recheios: recheiosDisponiveis });
      produtos.push({ id: 'tapioca3', nome: 'Tapioca 3 Recheios', preco: 19.00, img: 'https://i.pinimg.com/736x/23/45/4a/23454a1e2d9d8885839c89a71cd90cbf.jpg', categoria: '🫔 Monte a Sua Tapioca', tipo: 'montar', maxRecheios:3, minRecheios:2, recheios: recheiosDisponiveis });
      produtos.push({ id: 'tapioca4', nome: 'Tapioca 4 Recheios', preco: 21.00, img: 'https://i.pinimg.com/736x/23/45/4a/23454a1e2d9d8885839c89a71cd90cbf.jpg', categoria: '🫔 Monte a Sua Tapioca', tipo: 'montar', maxRecheios:4, minRecheios:3, recheios: recheiosDisponiveis });

      // 7. Novidade especiais (Mini pastéis pernambucanos)
      produtos.push({ id: 'mini-pasteis', nome: 'Mini Pastéis Pernambucanos (6und)', descricao: 'Recheados com carne, açúcar e canela', preco: 16.50, img: 'https://i.ytimg.com/vi/03C8mGqozSw/hq720.jpg', categoria: '✨ Novidade Especiais' });

      // 8. Batidas e Drinks (opcionais, com regra 500ml +5)
      const drinks = [
        { nome: 'Batidinha de Uva Cremosa', precoBase: 7.50, img:'https://i.pinimg.com/736x/12/99/22/1299226e7417a8c5bcdaf7d21a0ac45e.jpg' },
        { nome: 'Batidinha de Abacaxi Cremoso', precoBase:7.50, img:'https://i.pinimg.com/736x/e2/96/29/e2962983d1f17481a303aa9d5a506f3c.jpg' },
        { nome: 'Batidinha de Maracujá Cremoso', precoBase:9.50, img:'https://i.pinimg.com/736x/42/82/a9/4282a913d5a689015ecc849a6a27029b.jpg' },
        { nome: 'Batidinha de Morango Cremoso', precoBase:9.50, img:'https://i.pinimg.com/736x/f5/35/5a/f5355aa77f9f84ce9c48cdad0901598d.jpg' },
        { nome: 'Espanhola (Uva/Abacaxi/Leite condensado)', precoBase:7.50, img:'https://i.pinimg.com/736x/be/52/f9/be52f94c1721ef6e573bf97c56204c95.jpg' },
        { nome: 'Morancujá (Morango/Maracujá)', precoBase:9.50, img:'https://i.pinimg.com/736x/52/07/e3/5207e32580c9e67594e2eabafd60631d.jpg' },
        { nome: 'Morango com Abacaxi', precoBase:8.50, img:'https://i.pinimg.com/736x/52/07/e3/5207e32580c9e67594e2eabafd60631d.jpg' }
      ];
      drinks.forEach((d, idx) => {
        produtos.push({ ...d, id: `drink-300-${idx}`, preco: d.precoBase, descricao:'300ml', categoria:'🥤 Batidas e Drinks' });
        produtos.push({ ...d, id: `drink-500-${idx}`, preco: d.precoBase + 5, descricao:'500ml +R$5', categoria:'🥤 Batidas e Drinks' });
      });

      // 9. Acompanhamentos (porções) — simplificado
      const acompanhamentos = [
        { nome:'Batata Ondulada P', preco:12.50, img:'https://i.pinimg.com/736x/1e/b1/bb/1eb1bbf04ba24dbb9f0b1e8e8db2e719.jpg' },
        { nome:'Batata Ondulada M', preco:16.50, img:'https://i.pinimg.com/736x/1e/b1/bb/1eb1bbf04ba24dbb9f0b1e8e8db2e719.jpg' },
        { nome:'Batata Palito P', preco:10.00 },
        { nome:'Batata Palito M', preco:14.00 },
        { nome:'Bolinhas Carne Sol P', preco:12.00, img:'https://i.pinimg.com/736x/1e/b1/bb/1eb1bbf04ba24dbb9f0b1e8e8db2e719.jpg' },
        { nome:'Bolinhas Carne Sol M', preco:21.00, img:'https://i.pinimg.com/736x/1e/b1/bb/1eb1bbf04ba24dbb9f0b1e8e8db2e719.jpg' },
        { nome:'Mini Pastéis Pernambucanos (6und)', preco:9.50, img:'https://i.ytimg.com/vi/03C8mGqozSw/hq720.jpg' }
      ];
      acompanhamentos.forEach((a,idx) => produtos.push({ ...a, id: `acomp-${idx}`, categoria:'🍟 Acompanhamentos' }));

      // ---------- ESTADO GLOBAL ----------
      let carrinho = []; // { id, nome, preco, quantidade, observacao?, recheios?:[] }
      let pagamentoSelecionado = 'Pix';

      // ---------- RENDER CARDÁPIO ----------
      const cardapioEl = document.getElementById('cardapio');
      function renderCardapio() {
        const cats = [...new Set(produtos.map(p => p.categoria))];
        cardapioEl.innerHTML = cats.map(cat => {
          const prodCat = produtos.filter(p => p.categoria === cat);
          return `
            <div class="category">
              <h2>${cat}</h2>
              <div class="product-grid">
                ${prodCat.map(p => `
               
