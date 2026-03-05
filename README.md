<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
  <title>Cantinho do Sabor</title>
  <style>
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
      padding-bottom: 90px;
    }

    /* HERO */
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
      overflow: hidden;
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

    /* CARDÁPIO */
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

    .price {
      font-weight: 600;
      color: var(--orange-end);
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

    /* MODAL PRINCIPAL */
    .modal-overlay {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: rgba(0,0,0,0.5);
      display: none;
      align-items: center;
      justify-content: center;
      z-index: 3000;
      backdrop-filter: blur(4px);
    }

    .modal-content {
      background: white;
      width: 92%;
      max-width: 480px;
      max-height: 90vh;
      border-radius: 32px;
      padding: 24px;
      overflow-y: auto;
      box-shadow: var(--shadow-md);
      animation: slideUp 0.3s ease;
    }

    @keyframes slideUp {
      from { transform: translateY(60px); opacity: 0; }
      to { transform: translateY(0); opacity: 1; }
    }

    .modal-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 16px;
    }

    .close-modal {
      font-size: 28px;
      cursor: pointer;
      color: var(--gray-dark);
    }

    .recheio-group {
      margin: 20px 0;
      border: 1px solid var(--gray-medium);
      border-radius: 24px;
      padding: 16px;
    }

    .recheio-group h4 {
      margin-bottom: 12px;
      color: var(--orange-end);
    }

    .recheio-option {
      display: flex;
      align-items: center;
      gap: 8px;
      padding: 8px 0;
    }

    .recheio-option.disabled {
      opacity: 0.5;
      pointer-events: none;
    }

    .recheio-counter {
      font-size: 0.9rem;
      color: var(--orange-end);
      margin-bottom: 10px;
      font-weight: 600;
    }

    .extras-section {
      background: var(--gray-light);
      border-radius: 16px;
      padding: 16px;
      margin: 16px 0;
    }

    .extra-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 10px 0;
      border-bottom: 1px dashed var(--gray-medium);
    }

    .extra-item:last-child {
      border-bottom: none;
    }

    .extra-qtd {
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .extra-qtd button {
      width: 32px; height: 32px;
      border-radius: 50%;
      border: none;
      background: white;
      font-weight: bold;
      font-size: 1.2rem;
      box-shadow: var(--shadow-sm);
      cursor: pointer;
    }

    .extra-qtd button:active {
      background: var(--gray-medium);
    }

    .modal-footer {
      margin-top: 24px;
      display: flex;
      gap: 12px;
    }

    .btn-primary {
      flex: 1;
      background: linear-gradient(135deg, var(--orange-start), var(--orange-end));
      border: none;
      color: white;
      font-weight: 700;
      padding: 16px;
      border-radius: 40px;
      font-size: 1.1rem;
      cursor: pointer;
    }

    .btn-primary:disabled {
      opacity: 0.5;
      cursor: not-allowed;
    }

    .btn-secondary {
      background: var(--gray-light);
      border: none;
      padding: 16px;
      border-radius: 40px;
      font-weight: 600;
      cursor: pointer;
    }

    /* CARRINHO DRAWER */
    .cart-drawer {
      position: fixed;
      bottom: 0;
      left: 0;
      width: 100%;
      background: var(--white);
      border-top-left-radius: 24px;
      border-top-right-radius: 24px;
      box-shadow: 0 -8px 30px rgba(0,0,0,0.12);
      z-index: 2000;
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
    .cart-item-info { flex:1; font-size:0.95rem; }
    .cart-item-actions { display: flex; align-items: center; gap: 8px; }
    .cart-item-actions button {
      background: var(--gray-light);
      border: none;
      width: 30px; height: 30px;
      border-radius: 30px;
      font-weight: bold;
      font-size: 1.2rem;
      cursor: pointer;
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

    /* MODAL PIX */
    .pix-modal {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: rgba(0,0,0,0.5);
      display: none;
      align-items: center;
      justify-content: center;
      z-index: 4000;
    }
    .pix-content {
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
      font-size: 14px;
    }
    .copy-btn {
      background: var(--black);
      color: white;
      border: none;
      padding: 12px 24px;
      border-radius: 40px;
      font-weight: 600;
      cursor: pointer;
      margin-bottom: 10px;
      width: 100%;
    }
    .confirm-btn {
      background: linear-gradient(135deg, var(--orange-start), var(--orange-end));
      color: white;
      border: none;
      padding: 12px 24px;
      border-radius: 40px;
      font-weight: 600;
      cursor: pointer;
      width: 100%;
      margin-top: 10px;
    }

    /* MODAL CHECKOUT */
    .checkout-modal {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: rgba(0,0,0,0.5);
      display: none;
      align-items: center;
      justify-content: center;
      z-index: 3500;
    }
    .checkout-form {
      background: white;
      width: 92%;
      max-width: 480px;
      max-height: 90vh;
      border-radius: 32px;
      padding: 24px;
      overflow-y: auto;
    }
    .form-group {
      margin-bottom: 16px;
    }
    .form-group input, select, textarea {
      width: 100%;
      padding: 14px;
      border: 1px solid var(--gray-medium);
      border-radius: 40px;
      font-size: 1rem;
      font-family: 'Inter', sans-serif;
    }
    .form-group textarea {
      border-radius: 20px;
      resize: vertical;
    }
    #trocoField {
      margin-top: 8px;
      display: none;
    }
    .toast {
      position: fixed;
      bottom: 100px; left: 50%; transform: translateX(-50%);
      background: var(--black);
      color: white;
      padding: 8px 20px;
      border-radius: 40px;
      font-size: 0.9rem;
      opacity: 0;
      transition: opacity 0.2s;
      z-index: 5000;
    }

    .info-box {
      text-align: center;
      margin: 20px 0;
      padding: 15px;
      background: #f9f9f9;
      border-radius: 16px;
    }

    .info-box p {
      font-size: 1.2rem;
      font-weight: bold;
      color: #ff3d00;
    }

    .info-box .price-highlight {
      font-size: 1.1rem;
      margin-top: 10px;
      color: var(--black);
    }

    .endereco-row {
      display: flex;
      gap: 10px;
    }
    .endereco-row .form-group {
      flex: 1;
    }
  </style>
</head>
<body>
  <div class="hero">
    <div class="logo-wrapper">
      <img src="https://i.pinimg.com/736x/15/ac/c8/15acc8b00600f7f49f899cccbb55050d.jpg" alt="Cantinho do Sabor" onerror="this.src='https://via.placeholder.com/96x96?text=Cantinho'">
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

  <!-- MODAL DINÂMICO DE PRODUTO -->
  <div class="modal-overlay" id="productModal">
    <div class="modal-content" id="modalDynamicContent"></div>
  </div>

  <!-- MODAL PIX -->
  <div class="pix-modal" id="pixModal">
    <div class="pix-content">
      <h3>Pagamento PIX</h3>
      <p style="margin: 10px 0; color: #666;">Copie o código abaixo e pague no app do seu banco</p>
      <div class="pix-code" id="pixCode">82e5f2e0-772e-46d6-8ec9-3dbcf9b2c54c</div>
      <button class="copy-btn" id="copyPixBtn">📋 Copiar código</button>
      <button class="confirm-btn" id="confirmPixBtn">✅ Já fiz o pagamento</button>
      <p style="margin-top: 15px; font-size: 12px; color: #999;">Após copiar o código, confirme para enviar o pedido</p>
    </div>
  </div>

  <!-- MODAL CHECKOUT (DADOS) -->
  <div class="checkout-modal" id="checkoutModal">
    <div class="checkout-form" id="checkoutForm"></div>
  </div>

  <div class="toast" id="toast">Código copiado!</div>

  <script>
    (function() {
      const WHATSAPP_NUMBER = '5587933009283';
      
      const recheiosDisponiveis = [
        'Frango', 'Carne', 'Salsicha', 'Mussarela', 'Coalho', 'Milho', 'Azeitona',
        'Cream Cheese', 'Requeijão', 'Cheddar', 'Catupiry', 'Alho Frito', 'Pimenta Calabresa', 'Pernil'
      ];

      const acompanhamentos = [
        { nome: 'Batata Ondulada P', preco: 12.50 },
        { nome: 'Batata Ondulada M', preco: 16.50 },
        { nome: 'Batata Palito P', preco: 10.00 },
        { nome: 'Batata Palito M', preco: 14.00 },
        { nome: 'Bolinhas Carne Sol P', preco: 12.00 },
        { nome: 'Bolinhas Carne Sol M', preco: 21.00 },
        { nome: 'Mini Pastéis Pernambucanos (6und)', preco: 9.50 }
      ];

      const bebidas = [
        { nome: 'Batidinha Uva 300ml', preco: 7.50 },
        { nome: 'Batidinha Uva 500ml', preco: 12.50 },
        { nome: 'Batidinha Abacaxi 300ml', preco: 7.50 },
        { nome: 'Batidinha Abacaxi 500ml', preco: 12.50 },
        { nome: 'Batidinha Maracujá 300ml', preco: 9.50 },
        { nome: 'Batidinha Maracujá 500ml', preco: 14.50 },
        { nome: 'Espanhola 300ml', preco: 7.50 },
        { nome: 'Espanhola 500ml', preco: 12.50 },
        { nome: 'Morancujá 300ml', preco: 9.50 },
        { nome: 'Morancujá 500ml', preco: 14.50 }
      ];

      // Cardápio completo com as regras corretas
      const produtosBase = [
        { id: 'dueto', nome: 'Dueto Tradicional', preco: 22.50, img: 'https://i.pinimg.com/736x/c6/44/0a/c6440adee5ef7fa7d38f1e6e44f28be5.jpg', categoria: '🔥 Combos', tipo: 'dueto', recheiosObr: ['Frango','Carne','Mussarela','Coalho'] },
        
        // 🥟 Clássicos
        { id: 'caipira-especial', nome: 'Caipira Especial!', descricao: 'Frango e Milho', preco: 17.50, img: 'https://i.pinimg.com/736x/54/f3/3e/54f33e374276eb01904b8a7bfe94081e.jpg', categoria: '🥟 Clássicos', tipo: 'classico' },
        { id: 'queridinho', nome: 'O Queridinho!', descricao: 'Carne e Queijo', preco: 17.50, img: 'https://i.pinimg.com/736x/0e/ba/e1/0ebae10f386aaf02dda228b58951ce41.jpg', categoria: '🥟 Clássicos', tipo: 'classico' },
        { id: 'pastel-hotdog', nome: 'Pastel de Hotdog!', descricao: 'Salsicha, Carne e Cheddar', preco: 17.50, img: 'https://i.pinimg.com/736x/f6/ae/90/f6ae90345dc56319aa73d830743edb7f.jpg', categoria: '🥟 Clássicos', tipo: 'classico' },
        { id: 'frango-dourado', nome: 'Frango Dourado!', descricao: 'Frango e Queijo', preco: 18.00, img: 'https://i.pinimg.com/736x/90/7b/a5/907ba5cb7574a1ad9aa2eb0548c9eed4.jpg', categoria: '🥟 Clássicos', tipo: 'classico' },
        { id: 'mediterraneo', nome: 'Sabor Mediterrâneo', descricao: 'Carne e Azeitonas', preco: 18.00, img: 'https://i.pinimg.com/736x/8f/f6/b2/8ff6b260aa8709cce002ec39f97a464c.jpg', categoria: '🥟 Clássicos', tipo: 'classico' },
        { id: 'super-cremoso', nome: 'Super Cremoso', descricao: 'Frango e Requeijão', preco: 18.50, img: 'https://i.pinimg.com/736x/66/20/80/662080576d5755f1fb79d243117a37d8.jpg', categoria: '🥟 Clássicos', tipo: 'classico' },
        { id: 'frango-classico', nome: 'Frango Clássico', descricao: 'Frango, Catupiry e Milho', preco: 18.50, img: 'https://i.pinimg.com/736x/f4/29/44/f42944f3d798cf35a1e4fb028e62813a.jpg', categoria: '🥟 Clássicos', tipo: 'classico' },
        { id: 'cheddar-melt', nome: 'Cheddar Melt', descricao: 'Carne e Cheddar', preco: 18.50, img: 'https://i.pinimg.com/736x/3b/ee/28/3bee28d4d4e562a48782b3c1371d4009.jpg', categoria: '🥟 Clássicos', tipo: 'classico' },
        { id: 'trio-imperial', nome: 'Trio Imperial 3 Queijos', descricao: 'Mussarela, Coalho e Requeijão', preco: 18.50, img: 'https://i.pinimg.com/736x/25/44/bb/2544bb486fc56f83130814b41c27b0a9.jpg', categoria: '🥟 Clássicos', tipo: 'classico' },
        { id: 'pernil-cremoso', nome: 'Pernil Cremoso', descricao: 'Pernil, Catupiry e Milho', preco: 19.50, img: 'https://i.pinimg.com/736x/ee/65/0e/ee650e334bd5020ba51dfa1b32043d60.jpg', categoria: '🥟 Clássicos', tipo: 'classico' },
        { id: 'pernil-especial', nome: 'Pernil Especial', descricao: 'Pernil, Coalho e Requeijão', preco: 20.00, img: 'https://i.pinimg.com/736x/de/29/bf/de29bf0cfd6c1b1b2a52e37ea4e05c07.jpg', categoria: '🥟 Clássicos', tipo: 'classico' },
        { id: 'frango-gourmet', nome: 'Frango Gourmet', descricao: 'Cream Cheese e Azeitona', preco: 20.00, img: 'https://i.pinimg.com/736x/fb/c8/f4/fbc8f415a71bfb628aed9f182affe245.jpg', categoria: '🥟 Clássicos', tipo: 'classico' },
        { id: 'carne-completa', nome: 'Carne Completa', descricao: 'Queijo, Milho e Azeitona', preco: 20.00, img: 'https://i.pinimg.com/736x/e8/ed/20/e8ed20d0214d3033fdf86b708e2ac5fd.jpg', categoria: '🥟 Clássicos', tipo: 'classico' },
        
        // 🍧 Batidinhas de Açaí Gourmet
        { id: 'acai-300-1', nome: 'Batidinha de Açaí 300ml', descricao: '1 unidade (300ml)', preco: 14.90, img: 'https://i.pinimg.com/736x/cf/3e/ce/cf3eced59ad15ee6fc1ffb3ebe057cd6.jpg', categoria: '🍧 Batidinhas de Açaí Gourmet', tipo: 'acai', tamanho: '300ml', quantidade: 1 },
        { id: 'acai-300-2', nome: 'Batidinha de Açaí 300ml', descricao: 'Combo 2 unidades', preco: 26.00, img: 'https://i.pinimg.com/736x/cf/3e/ce/cf3eced59ad15ee6fc1ffb3ebe057cd6.jpg', categoria: '🍧 Batidinhas de Açaí Gourmet', tipo: 'acai', tamanho: '300ml', quantidade: 2 },
        { id: 'acai-300-3', nome: 'Batidinha de Açaí 300ml', descricao: 'Combo 3 unidades', preco: 36.00, img: 'https://i.pinimg.com/736x/cf/3e/ce/cf3eced59ad15ee6fc1ffb3ebe057cd6.jpg', categoria: '🍧 Batidinhas de Açaí Gourmet', tipo: 'acai', tamanho: '300ml', quantidade: 3 },
        { id: 'acai-500-1', nome: 'Batidinha de Açaí 500ml', descricao: '1 unidade (500ml)', preco: 22.00, img: 'https://i.pinimg.com/736x/cf/3e/ce/cf3eced59ad15ee6fc1ffb3ebe057cd6.jpg', categoria: '🍧 Batidinhas de Açaí Gourmet', tipo: 'acai', tamanho: '500ml', quantidade: 1 },
        { id: 'acai-500-2', nome: 'Batidinha de Açaí 500ml', descricao: 'Combo 2 unidades', preco: 39.90, img: 'https://i.pinimg.com/736x/cf/3e/ce/cf3eced59ad15ee6fc1ffb3ebe057cd6.jpg', categoria: '🍧 Batidinhas de Açaí Gourmet', tipo: 'acai', tamanho: '500ml', quantidade: 2 },
        { id: 'acai-500-3', nome: 'Batidinha de Açaí 500ml', descricao: 'Combo 3 unidades', preco: 57.00, img: 'https://i.pinimg.com/736x/cf/3e/ce/cf3eced59ad15ee6fc1ffb3ebe057cd6.jpg', categoria: '🍧 Batidinhas de Açaí Gourmet', tipo: 'acai', tamanho: '500ml', quantidade: 3 },
        
        // 🛠 Monte Pastel - CORRIGIDO: min 1, max específico
        { id: 'pastel2', nome: 'Pastel 2 Recheios', descricao: 'Escolha até 2 recheios (mínimo 1)', preco: 17.50, img: 'https://i.pinimg.com/736x/01/4e/04/014e04188feecfd5ea2ac209eb3ad09b.jpg', categoria: '🛠 Monte Pastel', tipo: 'montar', minRech: 1, maxRech: 2 },
        { id: 'pastel3', nome: 'Pastel 3 Recheios', descricao: 'Escolha até 3 recheios (mínimo 1)', preco: 19.50, img: 'https://i.pinimg.com/736x/01/4e/04/014e04188feecfd5ea2ac209eb3ad09b.jpg', categoria: '🛠 Monte Pastel', tipo: 'montar', minRech: 1, maxRech: 3 },
        { id: 'pastel4', nome: 'Pastel 4 Recheios', descricao: 'Escolha até 4 recheios (mínimo 1)', preco: 21.50, img: 'https://i.pinimg.com/736x/01/4e/04/014e04188feecfd5ea2ac209eb3ad09b.jpg', categoria: '🛠 Monte Pastel', tipo: 'montar', minRech: 1, maxRech: 4 },
        
        // 🌽 Monte Cuscuz - CORRIGIDO: min 1, max específico
        { id: 'cuscuz2', nome: 'Cuscuz 2 Recheios', descricao: 'Escolha até 2 recheios (mínimo 1)', preco: 16.50, img: 'https://i.pinimg.com/736x/b7/a1/a8/b7a1a8f4f27068bf9ab780cf38434bb0.jpg', categoria: '🌽 Monte Cuscuz', tipo: 'montar', minRech: 1, maxRech: 2 },
        { id: 'cuscuz3', nome: 'Cuscuz 3 Recheios', descricao: 'Escolha até 3 recheios (mínimo 1)', preco: 18.50, img: 'https://i.pinimg.com/736x/b7/a1/a8/b7a1a8f4f27068bf9ab780cf38434bb0.jpg', categoria: '🌽 Monte Cuscuz', tipo: 'montar', minRech: 1, maxRech: 3 },
        { id: 'cuscuz4', nome: 'Cuscuz 4 Recheios', descricao: 'Escolha até 4 recheios (mínimo 1)', preco: 20.50, img: 'https://i.pinimg.com/736x/b7/a1/a8/b7a1a8f4f27068bf9ab780cf38434bb0.jpg', categoria: '🌽 Monte Cuscuz', tipo: 'montar', minRech: 1, maxRech: 4 },
        
        // 🫔 Monte Tapioca - CORRIGIDO: min 1, max específico
        { id: 'tapioca2', nome: 'Tapioca 2 Recheios', descricao: 'Escolha até 2 recheios (mínimo 1)', preco: 17.00, img: 'https://i.pinimg.com/736x/23/45/4a/23454a1e2d9d8885839c89a71cd90cbf.jpg', categoria: '🫔 Monte Tapioca', tipo: 'montar', minRech: 1, maxRech: 2 },
        { id: 'tapioca3', nome: 'Tapioca 3 Recheios', descricao: 'Escolha até 3 recheios (mínimo 1)', preco: 19.00, img: 'https://i.pinimg.com/736x/23/45/4a/23454a1e2d9d8885839c89a71cd90cbf.jpg', categoria: '🫔 Monte Tapioca', tipo: 'montar', minRech: 1, maxRech: 3 },
        { id: 'tapioca4', nome: 'Tapioca 4 Recheios', descricao: 'Escolha até 4 recheios (mínimo 1)', preco: 21.00, img: 'https://i.pinimg.com/736x/23/45/4a/23454a1e2d9d8885839c89a71cd90cbf.jpg', categoria: '🫔 Monte Tapioca', tipo: 'montar', minRech: 1, maxRech: 4 },
        
        // ✨ Novidades
        { id: 'mini', nome: 'Mini Pastéis Pernambucanos', descricao: 'Porção com 6 unidades', preco: 16.50, img: 'https://i.ytimg.com/vi/03C8mGqozSw/hq720.jpg', categoria: '✨ Novidades', tipo: 'classico' }
      ];

      // Estado
      let carrinho = [];
      let dadosCliente = {};

      // Renderizar cardápio
      const cardapioEl = document.getElementById('cardapio');
      if (cardapioEl) {
        const cats = [...new Set(produtosBase.map(p => p.categoria))];
        cardapioEl.innerHTML = cats.map(cat => {
          const prodCat = produtosBase.filter(p => p.categoria === cat);
          return `
            <div class="category">
              <h2>${cat}</h2>
              <div class="product-grid">
                ${prodCat.map(p => `
                  <div class="product-card" data-id="${p.id}">
                    <img class="product-img" src="${p.img}" loading="lazy" onerror="this.src='https://via.placeholder.com/80x80?text=Produto'">
                    <div class="product-info">
                      <h3>${p.nome}</h3>
                      ${p.descricao ? `<div class="product-desc">${p.descricao}</div>` : ''}
                      <div class="product-footer">
                        <span class="price">R$ ${p.preco.toFixed(2)}</span>
                        <button class="add-btn" data-prod-id="${p.id}">+ adicionar</button>
                      </div>
                    </div>
                  </div>
                `).join('')}
              </div>
            </div>
          `;
        }).join('');
        console.log('Cardápio renderizado com', produtosBase.length, 'produtos');
      }

      function fecharModal() {
        document.getElementById('productModal').style.display = 'none';
      }

      function fecharCheckout() {
        document.getElementById('checkoutModal').style.display = 'none';
      }

      function atualizarCarrinho() {
        const cartItems = document.getElementById('cartItems');
        const itemCount = document.getElementById('itemCount');
        const subtotalEl = document.getElementById('subtotal');
        const totalEl = document.getElementById('total');
        const checkoutBtn = document.getElementById('checkoutBtn');
        
        itemCount.textContent = carrinho.length;
        
        let subtotal = 0;
        cartItems.innerHTML = carrinho.map((item, index) => {
          let itemTotal = item.preco;
          
          if (item.extras) {
            item.extras.forEach(ext => {
              itemTotal += ext.preco * ext.quantidade;
            });
          }
          
          subtotal += itemTotal;
          
          return `
            <div class="cart-item">
              <div class="cart-item-info">
                <strong>${item.nome}</strong>
                ${item.recheios ? `<br><small>Recheios: ${item.recheios.join(', ')}</small>` : ''}
                ${item.extras ? `<br><small>Extras: ${item.extras.map(e => `${e.nome} (${e.quantidade}x)`).join(', ')}</small>` : ''}
                <br><small>R$ ${itemTotal.toFixed(2)}</small>
              </div>
              <div class="cart-item-actions">
                <button onclick="removerItem(${index})">🗑️</button>
              </div>
            </div>
          `;
        }).join('');
        
        subtotalEl.textContent = subtotal.toFixed(2);
        totalEl.textContent = subtotal.toFixed(2);
        checkoutBtn.disabled = carrinho.length === 0;
      }

      window.removerItem = (index) => {
        carrinho.splice(index, 1);
        atualizarCarrinho();
      };

      window.fecharModal = fecharModal;
      window.fecharCheckout = fecharCheckout;

      // Função para controlar seleção de recheios em tempo real
      function setupRecheioValidation(maxRech) {
        const checkboxes = document.querySelectorAll('.recheio-check');
        const counterDiv = document.createElement('div');
        counterDiv.className = 'recheio-counter';
        counterDiv.textContent = `0/${maxRech} recheios selecionados`;
        
        const recheioGroup = document.querySelector('.recheio-group');
        if (recheioGroup) {
          recheioGroup.insertBefore(counterDiv, recheioGroup.querySelector('h4').nextSibling);
        }
        
        function updateCounter() {
          const checked = document.querySelectorAll('.recheio-check:checked').length;
          counterDiv.textContent = `${checked}/${maxRech} recheios selecionados`;
          
          // Desabilitar checkboxes não selecionados quando atingir o máximo
          if (checked >= maxRech) {
            checkboxes.forEach(cb => {
              if (!cb.checked) {
                cb.disabled = true;
                cb.closest('.recheio-option').classList.add('disabled');
              }
            });
          } else {
            checkboxes.forEach(cb => {
              cb.disabled = false;
              cb.closest('.recheio-option').classList.remove('disabled');
            });
          }
        }
        
        checkboxes.forEach(cb => {
          cb.addEventListener('change', updateCounter);
        });
        
        updateCounter();
      }

      function abrirModalProduto(prod) {
        const modalDiv = document.getElementById('modalDynamicContent');
        const modal = document.getElementById('productModal');
        
        let html = `<div class="modal-header"><h2>${prod.nome}</h2><span class="close-modal" onclick="fecharModal()">&times;</span></div>`;
        
        if (prod.tipo === 'acai') {
          html += `
            <div class="info-box">
              <p>${prod.tamanho}</p>
              <p class="price-highlight">${prod.quantidade} unidade${prod.quantidade > 1 ? 's' : ''}</p>
              <p class="price-highlight">Preço: R$ ${prod.preco.toFixed(2)}</p>
            </div>
          `;
        }
        
        if (prod.tipo === 'dueto') {
          html += `
            <div class="recheio-group">
              <h4>Escolha o Recheio do 1° Pastel!</h4>
              ${prod.recheiosObr.map(r => `<label class="recheio-option"><input type="radio" name="recheio1" value="${r}" required> ${r}</label>`).join('')}
            </div>
            <div class="recheio-group">
              <h4>Escolha o Recheio do 2° Pastel!</h4>
              ${prod.recheiosObr.map(r => `<label class="recheio-option"><input type="radio" name="recheio2" value="${r}" required> ${r}</label>`).join('')}
            </div>
          `;
        } else if (prod.tipo === 'montar') {
          html += `<div class="recheio-group" data-max="${prod.maxRech}"><h4>Selecione os recheios (mínimo ${prod.minRech} • máximo ${prod.maxRech})</h4>`;
          recheiosDisponiveis.forEach(r => {
            html += `<label class="recheio-option"><input type="checkbox" class="recheio-check" value="${r}"> ${r}</label>`;
          });
          html += `</div>`;
        }
        
        html += `
          <div class="extras-section">
            <h4>Acompanhamentos</h4>
            ${acompanhamentos.map((ext, idx) => `
              <div class="extra-item">
                <span>${ext.nome} - R$ ${ext.preco.toFixed(2)}</span>
                <div class="extra-qtd">
                  <button class="dec-extra" data-index="${idx}" data-tipo="acomp">-</button>
                  <span id="qtd-acomp-${idx}">0</span>
                  <button class="inc-extra" data-index="${idx}" data-tipo="acomp">+</button>
                </div>
              </div>
            `).join('')}
            
            <h4 style="margin-top: 16px;">Bebidas</h4>
            ${bebidas.map((ext, idx) => `
              <div class="extra-item">
                <span>${ext.nome} - R$ ${ext.preco.toFixed(2)}</span>
                <div class="extra-qtd">
                  <button class="dec-extra" data-index="${idx}" data-tipo="bebida">-</button>
                  <span id="qtd-bebida-${idx}">0</span>
                  <button class="inc-extra" data-index="${idx}" data-tipo="bebida">+</button>
                </div>
              </div>
            `).join('')}
          </div>
          
          <div class="modal-footer">
            <button class="btn-secondary" onclick="fecharModal()">Cancelar</button>
            <button class="btn-primary" id="adicionarAoCarrinho">Adicionar · R$ ${prod.preco.toFixed(2)}</button>
          </div>
        `;
        
        modalDiv.innerHTML = html;
        modal.style.display = 'flex';
        
        // Configurar validação de recheios em tempo real para produtos do tipo 'montar'
        if (prod.tipo === 'montar') {
          setupRecheioValidation(prod.maxRech);
        }
        
        // Eventos extras
        document.querySelectorAll('.inc-extra').forEach(btn => {
          btn.addEventListener('click', (e) => {
            const index = e.target.dataset.index;
            const tipo = e.target.dataset.tipo;
            const span = document.getElementById(`qtd-${tipo}-${index}`);
            if (span) span.textContent = parseInt(span.textContent) + 1;
          });
        });
        
        document.querySelectorAll('.dec-extra').forEach(btn => {
          btn.addEventListener('click', (e) => {
            const index = e.target.dataset.index;
            const tipo = e.target.dataset.tipo;
            const span = document.getElementById(`qtd-${tipo}-${index}`);
            if (span) {
              const valor = parseInt(span.textContent);
              if (valor > 0) span.textContent = valor - 1;
            }
          });
        });
        
        document.getElementById('adicionarAoCarrinho').addEventListener('click', () => {
          adicionarAoCarrinho(prod);
        });
      }

      function adicionarAoCarrinho(prod) {
        let recheios = [];
        
        if (prod.tipo === 'dueto') {
          const recheio1 = document.querySelector('input[name="recheio1"]:checked')?.value;
          const recheio2 = document.querySelector('input[name="recheio2"]:checked')?.value;
          if (recheio1 && recheio2) {
            recheios = [recheio1, recheio2];
          } else {
            alert('Selecione ambos os recheios!');
            return;
          }
        } else if (prod.tipo === 'montar') {
          const checks = document.querySelectorAll('.recheio-check:checked');
          recheios = Array.from(checks).map(c => c.value);
          
          // Validação rigorosa
          if (recheios.length < prod.minRech) {
            alert(`Selecione pelo menos ${prod.minRech} recheio${prod.minRech > 1 ? 's' : ''}!`);
            return;
          }
          if (recheios.length > prod.maxRech) {
            alert(`Selecione no máximo ${prod.maxRech} recheios!`);
            return;
          }
        }
        
        const extras = [];
        
        acompanhamentos.forEach((ext, idx) => {
          const qtd = parseInt(document.getElementById(`qtd-acomp-${idx}`)?.textContent || '0');
          if (qtd > 0) {
            extras.push({
              nome: ext.nome,
              preco: ext.preco,
              quantidade: qtd
            });
          }
        });
        
        bebidas.forEach((ext, idx) => {
          const qtd = parseInt(document.getElementById(`qtd-bebida-${idx}`)?.textContent || '0');
          if (qtd > 0) {
            extras.push({
              nome: ext.nome,
              preco: ext.preco,
              quantidade: qtd
            });
          }
        });
        
        const itemCarrinho = {
          id: prod.id + Date.now(),
          nome: prod.nome,
          preco: prod.preco,
          quantidade: 1,
          recheios: recheios.length > 0 ? recheios : null,
          extras: extras.length > 0 ? extras : null
        };
        
        carrinho.push(itemCarrinho);
        atualizarCarrinho();
        fecharModal();
        document.getElementById('cartDrawer').classList.remove('collapsed');
      }

      function enviarParaWhatsApp(nome, logradouro, numero, complemento, referencia, pagamento, troco, observacoes, total) {
        let enderecoCompleto = `${logradouro}, ${numero}`;
        if (complemento) enderecoCompleto += ` - ${complemento}`;

        let mensagem = `NOVO PEDIDO!\n`;
        mensagem += `Cliente: ${nome}\n`;
        mensagem += `Endereço: ${enderecoCompleto}\n`;
        mensagem += `Ponto de Referência: ${referencia || 'Não informado'}\n`;
        
        let formaPagamento = pagamento === 'dinheiro' ? 'Dinheiro' : 
                            pagamento === 'cartao' ? 'Cartão' : 'PIX';
        if (pagamento === 'dinheiro' && troco) {
          formaPagamento += ` (Troco para R$ ${troco})`;
        }
        mensagem += `Forma de Pagamento: ${formaPagamento}\n`;
        mensagem += `ITENS:\n`;
        
        carrinho.forEach(item => {
          mensagem += `° 1x ${item.nome}, R$ ${item.preco.toFixed(2)}\n`;
          if (item.recheios?.length) {
            mensagem += `   Recheios: ${item.recheios.join(', ')}\n`;
          }
          if (item.extras?.length) {
            item.extras.forEach(ext => {
              mensagem += `   + ${ext.quantidade}x ${ext.nome} - R$ ${(ext.preco * ext.quantidade).toFixed(2)}\n`;
            });
          }
        });
        
        mensagem += `TOTAL: R$ ${total.toFixed(2)}`;
        if (observacoes) mensagem += `\n\nObservações: ${observacoes}`;

        window.open(`https://wa.me/${WHATSAPP_NUMBER}?text=${encodeURIComponent(mensagem)}`, '_blank');
        carrinho = [];
        atualizarCarrinho();
      }

      function abrirModalCheckout() {
        const checkoutForm = document.getElementById('checkoutForm');
        const modal = document.getElementById('checkoutModal');
        
        checkoutForm.innerHTML = `
          <h2 style="margin-bottom: 20px;">Finalizar Pedido</h2>
          <div class="form-group">
            <input type="text" placeholder="Nome completo" id="nomeCliente" required value="${dadosCliente.nome || ''}">
          </div>
          <div class="form-group">
            <input type="text" placeholder="Rua/Logradouro" id="logradouro" required value="${dadosCliente.logradouro || ''}">
          </div>
          <div class="endereco-row">
            <div class="form-group">
              <input type="text" placeholder="Número" id="numero" required value="${dadosCliente.numero || ''}">
            </div>
            <div class="form-group">
              <input type="text" placeholder="Complemento" id="complemento" value="${dadosCliente.complemento || ''}">
            </div>
          </div>
          <div class="form-group">
            <input type="text" placeholder="Ponto de referência" id="referencia" value="${dadosCliente.referencia || ''}">
          </div>
          <div class="form-group">
            <select id="pagamento">
              <option value="dinheiro" ${dadosCliente.pagamento === 'dinheiro' ? 'selected' : ''}>Dinheiro</option>
              <option value="cartao" ${dadosCliente.pagamento === 'cartao' ? 'selected' : ''}>Cartão de Crédito/Débito</option>
              <option value="pix" ${dadosCliente.pagamento === 'pix' ? 'selected' : ''}>PIX</option>
            </select>
          </div>
          <div id="trocoField" class="form-group" style="display: ${dadosCliente.pagamento === 'dinheiro' ? 'block' : 'none'};">
            <input type="text" placeholder="Precisa de troco para quanto?" id="troco" value="${dadosCliente.troco || ''}">
          </div>
          <div class="form-group">
            <textarea placeholder="Observações (opcional)" id="observacoes" rows="3">${dadosCliente.observacoes || ''}</textarea>
          </div>
          <div style="display: flex; gap: 12px;">
            <button class="btn-secondary" onclick="fecharCheckout()">Cancelar</button>
            <button class="btn-primary" onclick="processarCheckout()">Confirmar Pedido</button>
          </div>
        `;
        
        modal.style.display = 'flex';
        
        document.getElementById('pagamento').addEventListener('change', (e) => {
          const trocoField = document.getElementById('trocoField');
          trocoField.style.display = e.target.value === 'dinheiro' ? 'block' : 'none';
        });
      }

      window.processarCheckout = () => {
        const nome = document.getElementById('nomeCliente')?.value;
        const logradouro = document.getElementById('logradouro')?.value;
        const numero = document.getElementById('numero')?.value;
        const complemento = document.getElementById('complemento')?.value || '';
        const referencia = document.getElementById('referencia')?.value || '';
        const pagamento = document.getElementById('pagamento')?.value;
        const troco = document.getElementById('troco')?.value || '';
        const observacoes = document.getElementById('observacoes')?.value || '';

        if (!nome || !logradouro || !numero) {
          alert('Por favor, preencha todos os campos obrigatórios!');
          return;
        }

        dadosCliente = { nome, logradouro, numero, complemento, referencia, pagamento, troco, observacoes };

        const total = carrinho.reduce((acc, item) => {
          let itemTotal = item.preco;
          if (item.extras) {
            item.extras.forEach(ext => itemTotal += ext.preco * ext.quantidade);
          }
          return acc + itemTotal;
        }, 0);

        if (pagamento === 'pix') {
          fecharCheckout();
          document.getElementById('pixModal').style.display = 'flex';
        } else {
          enviarParaWhatsApp(nome, logradouro, numero, complemento, referencia, pagamento, troco, observacoes, total);
          fecharCheckout();
        }
      };

      // Event listeners
      document.addEventListener('click', (e) => {
        if (e.target.classList.contains('add-btn')) {
          const prodId = e.target.dataset.prodId;
          const produto = produtosBase.find(p => p.id === prodId);
          if (produto) abrirModalProduto(produto);
        }
      });

      document.getElementById('cartHandle').addEventListener('click', () => {
        const drawer = document.getElementById('cartDrawer');
        drawer.classList.toggle('collapsed');
        const toggle = document.getElementById('drawerToggle');
        toggle.textContent = drawer.classList.contains('collapsed') ? '▲' : '▼';
      });

      document.getElementById('checkoutBtn').addEventListener('click', abrirModalCheckout);

      // PIX
      document.getElementById('copyPixBtn').addEventListener('click', () => {
        const pixCode = document.getElementById('pixCode').textContent;
        navigator.clipboard.writeText(pixCode).then(() => {
          const toast = document.getElementById('toast');
          toast.textContent = 'Código copiado!';
          toast.style.opacity = '1';
          setTimeout(() => toast.style.opacity = '0', 2000);
        });
      });

      document.getElementById('confirmPixBtn').addEventListener('click', () => {
        enviarParaWhatsApp(
          dadosCliente.nome,
          dadosCliente.logradouro,
          dadosCliente.numero,
          dadosCliente.complemento,
          dadosCliente.referencia,
          dadosCliente.pagamento,
          dadosCliente.troco,
          dadosCliente.observacoes,
          parseFloat(document.getElementById('total').textContent)
        );
        document.getElementById('pixModal').style.display = 'none';
        
        const toast = document.getElementById('toast');
        toast.textContent = 'Pedido enviado com sucesso!';
        toast.style.opacity = '1';
        setTimeout(() => toast.style.opacity = '0', 3000);
      });

      // Fechar modais
      document.getElementById('productModal').addEventListener('click', (e) => {
        if (e.target === document.getElementById('productModal')) fecharModal();
      });

      document.getElementById('pixModal').addEventListener('click', (e) => {
        if (e.target === document.getElementById('pixModal')) {
          document.getElementById('pixModal').style.display = 'none';
        }
      });

      document.getElementById('checkoutModal').addEventListener('click', (e) => {
        if (e.target === document.getElementById('checkoutModal')) fecharCheckout();
      });
    })();
  </script>
</body>
</html>
