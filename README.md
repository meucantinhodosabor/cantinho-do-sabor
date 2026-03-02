<!DOCTYPE html>
<html lang="pt-br">
<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Cantinho do Sabor</title>

<style>

:root{
--primary:#ff7b00;
}

body{
margin:0;
font-family:Arial;
background:#f7f7f7;
}

header{
background:var(--primary);
color:white;
padding:18px;
text-align:center;
font-size:22px;
font-weight:bold;
}

.container{
padding:15px;
}

.category{
margin-top:30px;
}

.product{
display:flex;
gap:12px;
background:white;
padding:10px;
border-radius:12px;
margin-bottom:10px;
box-shadow:0 2px 6px rgba(0,0,0,0.08);
}

.product img{
width:90px;
height:90px;
border-radius:10px;
object-fit:cover;
}

.info{
flex:1;
}

.name{
font-weight:bold;
font-size:16px;
}

.desc{
font-size:13px;
color:#777;
}

.price{
font-weight:bold;
margin-top:4px;
}

.controls{
display:flex;
align-items:center;
gap:8px;
margin-top:5px;
}

.controls button{
width:28px;
height:28px;
border:none;
background:var(--primary);
color:white;
border-radius:50%;
font-size:16px;
cursor:pointer;
}

.cart{
position:fixed;
bottom:0;
left:0;
right:0;
background:white;
padding:15px;
box-shadow:0 -2px 10px rgba(0,0,0,0.15);
display:flex;
justify-content:space-between;
align-items:center;
}

.cart button{
background:var(--primary);
color:white;
border:none;
padding:10px 16px;
border-radius:8px;
font-weight:bold;
cursor:pointer;
}

</style>

</head>

<body>

<header>
Cantinho do Sabor
</header>

<div class="container">

<!-- COMBOS -->

<div class="category">

<h2>Combos Promocionais</h2>

<div class="product">
<img src="https://images.unsplash.com/photo-1604908176997-4310b73a91b2">
<div class="info">
<div class="name">Dueto Tradicional</div>
<div class="desc">2 Pastéis de 1 recheio (Carne, Mussarela, Coalho ou Frango)</div>
<div class="price">R$22,50</div>
<div class="controls">
<button onclick="removeItem('Dueto Tradicional',22.5)">-</button>
<span id="Dueto Tradicional">0</span>
<button onclick="addItem('Dueto Tradicional',22.5)">+</button>
</div>
</div>
</div>

</div>

<!-- PASTÉIS -->

<div class="category">

<h2>Clássicos Inesquecíveis</h2>

<div class="product">
<img src="https://images.unsplash.com/photo-1601050690597-df0568f70950">
<div class="info">
<div class="name">Caipira Especial</div>
<div class="desc">Frango e milho</div>
<div class="price">R$17,50</div>
<div class="controls">
<button onclick="removeItem('Caipira Especial',17.5)">-</button>
<span id="Caipira Especial">0</span>
<button onclick="addItem('Caipira Especial',17.5)">+</button>
</div>
</div>
</div>

<div class="product">
<img src="https://images.unsplash.com/photo-1612392062798-2c0c6fcb1e0a">
<div class="info">
<div class="name">O Queridinho</div>
<div class="desc">Carne e queijo</div>
<div class="price">R$17,50</div>
<div class="controls">
<button onclick="removeItem('O Queridinho',17.5)">-</button>
<span id="O Queridinho">0</span>
<button onclick="addItem('O Queridinho',17.5)">+</button>
</div>
</div>
</div>

</div>

<!-- ACOMPANHAMENTOS -->

<div class="category">

<h2>Acompanhamentos</h2>

<div class="product">
<img src="https://images.unsplash.com/photo-1576107232684-1279f390859f">
<div class="info">
<div class="name">Batata Frita Ondulada P</div>
<div class="price">R$12,50</div>
<div class="controls">
<button onclick="removeItem('Batata P',12.5)">-</button>
<span id="Batata P">0</span>
<button onclick="addItem('Batata P',12.5)">+</button>
</div>
</div>
</div>

<div class="product">
<img src="https://images.unsplash.com/photo-1576107232684-1279f390859f">
<div class="info">
<div class="name">Batata Frita Ondulada M</div>
<div class="price">R$16,50</div>
<div class="controls">
<button onclick="removeItem('Batata M',16.5)">-</button>
<span id="Batata M">0</span>
<button onclick="addItem('Batata M',16.5)">+</button>
</div>
</div>
</div>

</div>

<!-- SOBREMESA -->

<div class="category">

<h2>Sobremesas</h2>

<div class="product">
<img src="https://i.ytimg.com/vi/03C8mGqozSw/hq720.jpg">
<div class="info">
<div class="name">Mini Pastéis Pernambucanos</div>
<div class="desc">6 unidades</div>
<div class="price">R$16,50</div>
<div class="controls">
<button onclick="removeItem('Mini Pastel',16.5)">-</button>
<span id="Mini Pastel">0</span>
<button onclick="addItem('Mini Pastel',16.5)">+</button>
</div>
</div>
</div>

</div>

</div>

<div class="cart">

<div>

Total: R$ <span id="total">0.00</span>

</div>

<button onclick="enviarPedido()">
Enviar Pedido
</button>

</div>

<script>

let cart={}
let total=0

function addItem(nome,preco){

if(!cart[nome]) cart[nome]=0

cart[nome]++

total+=preco

document.getElementById(nome).innerText=cart[nome]

document.getElementById("total").innerText=total.toFixed(2)

}

function removeItem(nome,preco){

if(cart[nome]){

cart[nome]--

total-=preco

if(cart[nome]<0) cart[nome]=0

if(total<0) total=0

document.getElementById(nome).innerText=cart[nome]

document.getElementById("total").innerText=total.toFixed(2)

}

}

function enviarPedido(){

let mensagem="Pedido:%0A"

for(let item in cart){

if(cart[item]>0){

mensagem+=item+" x"+cart[item]+"%0A"

}

}

mensagem+="Total: R$ "+total.toFixed(2)

window.open("https://wa.me/5587933009283?text="+mensagem)

}

</script>

</body>
</html>
