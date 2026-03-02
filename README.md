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
margin-top:25px;
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

.price{
font-weight:bold;
margin-top:5px;
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

<div class="category">

<h2>Combos Promocionais</h2>

<div class="product">

<img src="https://pin.it/5DyjyI6cH">

<div class="info">

<div class="name">Dueto Tradicional</div>

<div>2 Pastéis de 1 recheio</div>

<div class="price">R$22.50</div>

<div class="controls">

<button onclick="removeItem('Dueto Tradicional',22.5)">-</button>

<span id="Dueto Tradicional">0</span>

<button onclick="addItem('Dueto Tradicional',22.5)">+</button>

</div>

</div>

</div>

</div>

<div class="category">

<h2>Clássicos Inesquecíveis</h2>

<div class="product">

<img src="https://pin.it/53c3Or9hA">

<div class="info">

<div class="name">Caipira Especial</div>

<div class="price">R$17.50</div>

<div class="controls">

<button onclick="removeItem('Caipira Especial',17.5)">-</button>

<span id="Caipira Especial">0</span>

<button onclick="addItem('Caipira Especial',17.5)">+</button>

</div>

</div>

</div>

<div class="product">

<img src="https://pin.it/ardDy0C3U">

<div class="info">

<div class="name">O Queridinho</div>

<div class="price">R$17.50</div>

<div class="controls">

<button onclick="removeItem('O Queridinho',17.5)">-</button>

<span id="O Queridinho">0</span>

<button onclick="addItem('O Queridinho',17.5)">+</button>

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

mensagem+= item + " x" + cart[item] + "%0A"

}

}

mensagem+="Total: R$ " + total.toFixed(2)

window.open("https://wa.me/5587933009283?text=" + mensagem)

}

</script>

</body>
</html>
