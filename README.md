<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cantinho do Sabor</title>

<style>
body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #f8f8f8;
}

header {
    background: #ff6600;
    color: white;
    text-align: center;
    padding: 15px;
    font-size: 1.4rem;
    font-weight: bold;
}

.container {
    padding: 15px;
}

.card {
    background: white;
    border-radius: 10px;
    padding: 15px;
    margin-bottom: 15px;
    box-shadow: 0 3px 10px rgba(0,0,0,0.08);
}

.card h3 {
    margin: 0 0 5px 0;
}

.card button {
    background: #ff6600;
    color: white;
    border: none;
    padding: 8px 12px;
    border-radius: 6px;
    cursor: pointer;
    margin-top: 8px;
}

#cart-bar {
    position: fixed;
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%);
    background: #222;
    color: white;
    padding: 12px 20px;
    border-radius: 30px;
    display: none;
    justify-content: space-between;
    width: 85%;
    max-width: 400px;
    cursor: pointer;
}

#cart-modal {
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.5);
    display: none;
    justify-content: center;
    align-items: center;
}

.modal-content {
    background: white;
    width: 90%;
    max-width: 400px;
    border-radius: 10px;
    padding: 15px;
}

.cart-item {
    display: flex;
    justify-content: space-between;
    margin-bottom: 10px;
}

.cart-controls button {
    margin: 0 5px;
}

.close {
    text-align: right;
    cursor: pointer;
    font-weight: bold;
}
</style>
</head>

<body>

<header>Cantinho do Sabor</header>

<div class="container">

<div class="card">
<h3>Pastel de Carne</h3>
<p>R$ 10.00</p>
<button onclick="addToCart('Pastel de Carne',10)">Adicionar</button>
</div>

<div class="card">
<h3>Pastel de Queijo</h3>
<p>R$ 9.00</p>
<button onclick="addToCart('Pastel de Queijo',9)">Adicionar</button>
</div>

<div class="card">
<h3>Refrigerante Lata</h3>
<p>R$ 6.00</p>
<button onclick="addToCart('Refrigerante Lata',6)">Adicionar</button>
</div>

</div>

<!-- Barra do Carrinho -->
<div id="cart-bar" onclick="abrirSacola()">
<span id="c-qty">0 itens</span>
<span id="c-total">R$ 0.00</span>
</div>

<!-- Modal -->
<div id="cart-modal">
<div class="modal-content">
<div class="close" onclick="fecharSacola()">X</div>

<h3>Sua Sacola</h3>
<div id="cart-items"></div>

<p id="info-entrega">🚚 Entrega Grátis aplicada!</p>

<h3>Total: <span id="f-total">R$ 0.00</span></h3>

<button onclick="finalizarPedido()" style="width:100%;margin-top:10px;background:#25D366;">
Finalizar pelo WhatsApp
</button>

</div>
</div>

<script>
let cart = [];

// Adicionar
function addToCart(nome, preco){
    const item = cart.find(i => i.nome === nome);
    if(item){
        item.qtd++;
    } else {
        cart.push({nome, preco, qtd:1});
    }
    atualizarUI();
}

// Alterar quantidade
function alterarQtd(nome, tipo){
    const item = cart.find(i => i.nome === nome);
    if(!item) return;

    if(tipo === 'mais'){
        item.qtd++;
    } else {
        item.qtd--;
        if(item.qtd <= 0){
            cart = cart.filter(i => i.nome !== nome);
        }
    }
    atualizarUI();
}

// Atualizar interface
function atualizarUI(){
    let total = 0;
    let qtdTotal = 0;
    const lista = document.getElementById("cart-items");
    lista.innerHTML = "";

    cart.forEach(item=>{
        total += item.preco * item.qtd;
        qtdTotal += item.qtd;

        lista.innerHTML += `
        <div class="cart-item">
            <div>
                ${item.nome}<br>
                R$ ${item.preco.toFixed(2)}
            </div>
            <div class="cart-controls">
                <button onclick="alterarQtd('${item.nome}','menos')">-</button>
                ${item.qtd}
                <button onclick="alterarQtd('${item.nome}','mais')">+</button>
            </div>
        </div>
        `;
    });

    document.getElementById("c-qty").innerText = qtdTotal + (qtdTotal === 1 ? " item" : " itens");
    document.getElementById("c-total").innerText = "R$ " + total.toFixed(2);
    document.getElementById("f-total").innerText = "R$ " + total.toFixed(2);

    document.getElementById("cart-bar").style.display = qtdTotal > 0 ? "flex" : "none";
}

// Abrir/Fechar
function abrirSacola(){
    document.getElementById("cart-modal").style.display = "flex";
}

function fecharSacola(){
    document.getElementById("cart-modal").style.display = "none";
}

// Finalizar
function finalizarPedido(){
    if(cart.length === 0) return;

    let mensagem = "🛒 *Novo Pedido - Cantinho do Sabor*%0A%0A";

    cart.forEach(item=>{
        mensagem += `• ${item.nome} (${item.qtd}x) - R$ ${(item.preco*item.qtd).toFixed(2)}%0A`;
    });

    const total = cart.reduce((acc,item)=>acc + item.preco*item.qtd,0);

    mensagem += `%0A🚚 Entrega: GRÁTIS`;
    mensagem += `%0A💰 *Total: R$ ${total.toFixed(2)}*`;

    window.open(`https://wa.me/5587933009283?text=${mensagem}`,"_blank");
}
</script>

</body>
</html>
