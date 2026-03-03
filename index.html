<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cantinho do Sabor</title>

<style>
body{
    margin:0;
    font-family:Arial, sans-serif;
    background:#f4f4f4;
}

header{
    background:#ff6600;
    color:white;
    text-align:center;
    padding:15px;
    font-size:20px;
    font-weight:bold;
}

.container{
    padding:15px;
}

.card{
    background:white;
    padding:15px;
    border-radius:8px;
    margin-bottom:15px;
    box-shadow:0 3px 8px rgba(0,0,0,0.1);
}

.card button{
    background:#ff6600;
    color:white;
    border:none;
    padding:8px 12px;
    border-radius:5px;
    cursor:pointer;
    margin-top:8px;
}

#cart-bar{
    position:fixed;
    bottom:20px;
    left:50%;
    transform:translateX(-50%);
    background:#222;
    color:white;
    padding:12px 20px;
    border-radius:30px;
    display:none;
    justify-content:space-between;
    width:90%;
    max-width:400px;
    cursor:pointer;
}

#cart-modal{
    position:fixed;
    inset:0;
    background:rgba(0,0,0,0.5);
    display:none;
    justify-content:center;
    align-items:center;
}

.modal-content{
    background:white;
    width:90%;
    max-width:400px;
    border-radius:8px;
    padding:15px;
}

.cart-item{
    display:flex;
    justify-content:space-between;
    margin-bottom:10px;
}

.cart-controls button{
    margin:0 5px;
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

<div id="cart-bar" onclick="abrirSacola()">
<span id="c-qty">0 itens</span>
<span id="c-total">R$ 0.00</span>
</div>

<div id="cart-modal">
<div class="modal-content">
<h3>Sua Sacola</h3>
<div id="cart-items"></div>
<p>🚚 Entrega Grátis</p>
<h3>Total: <span id="f-total">R$ 0.00</span></h3>
<button onclick="finalizarPedido()" style="width:100%;background:#25D366;color:white;padding:10px;border:none;border-radius:5px;">
Finalizar pelo WhatsApp
</button>
<button onclick="fecharSacola()" style="width:100%;margin-top:5px;">Fechar</button>
</div>
</div>

<script>

let cart = [];

function addToCart(nome, preco){
    const item = cart.find(p => p.nome === nome);
    if(item){
        item.qtd++;
    } else {
        cart.push({nome:nome, preco:preco, qtd:1});
    }
    atualizar();
}

function alterar(nome, tipo){
    const item = cart.find(p => p.nome === nome);
    if(!item) return;

    if(tipo === "mais"){
        item.qtd++;
    } else {
        item.qtd--;
        if(item.qtd <= 0){
            cart = cart.filter(p => p.nome !== nome);
        }
    }
    atualizar();
}

function atualizar(){
    let total = 0;
    let qtd = 0;

    const lista = document.getElementById("cart-items");
    lista.innerHTML = "";

    cart.forEach(item=>{
        total += item.preco * item.qtd;
        qtd += item.qtd;

        lista.innerHTML += `
        <div class="cart-item">
            <div>
                ${item.nome}<br>
                R$ ${item.preco.toFixed(2)}
            </div>
            <div class="cart-controls">
                <button onclick="alterar('${item.nome}','menos')">-</button>
                ${item.qtd}
                <button onclick="alterar('${item.nome}','mais')">+</button>
            </div>
        </div>
        `;
    });

    document.getElementById("c-qty").innerText = qtd + " item(ns)";
    document.getElementById("c-total").innerText = "R$ " + total.toFixed(2);
    document.getElementById("f-total").innerText = "R$ " + total.toFixed(2);

    document.getElementById("cart-bar").style.display = qtd > 0 ? "flex" : "none";
}

function abrirSacola(){
    document.getElementById("cart-modal").style.display = "flex";
}

function fecharSacola(){
    document.getElementById("cart-modal").style.display = "none";
}

function finalizarPedido(){
    if(cart.length === 0) return;

    let mensagem = "🛒 *Novo Pedido - Cantinho do Sabor*%0A%0A";

    cart.forEach(item=>{
        mensagem += `• ${item.nome} (${item.qtd}x) - R$ ${(item.preco*item.qtd).toFixed(2)}%0A`;
    });

    const total = cart.reduce((acc,item)=>acc + item.preco*item.qtd,0);

    mensagem += `%0A🚚 Entrega: GRÁTIS`;
    mensagem += `%0A💰 *Total: R$ ${total.toFixed(2)}*`;

    window.open("https://wa.me/5587933009283?text="+mensagem, "_blank");
}

</script>

</body>
</html>
