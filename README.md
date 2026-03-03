<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cantinho do Sabor</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<style>
*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:'Poppins',sans-serif;
}

body{
background:#f5f5f5;
}

/* CAPA */
.header{
width:100%;
height:220px;
background:url('https://i.pinimg.com/736x/c6/44/0a/c6440adee5ef7fa7d38f1e6e44f28be5.jpg') center/cover no-repeat;
position:relative;
}

/* CARD LOJA */
.store-card{
position:relative;
margin-top:-70px;
background:#fff;
border-radius:25px 25px 0 0;
padding:70px 20px 20px 20px;
box-shadow:0 -5px 20px rgba(0,0,0,0.08);
}

/* LOGO REDONDA */
.store-logo{
position:absolute;
top:-60px;
left:50%;
transform:translateX(-50%);
width:110px;
height:110px;
border-radius:50%;
border:5px solid white;
background:url('https://i.pinimg.com/736x/15/ac/c8/15acc8b00600f7f49f899cccbb55050d.jpg') center/cover no-repeat;
box-shadow:0 5px 15px rgba(0,0,0,0.2);
}

.store-name{
text-align:center;
font-size:22px;
font-weight:700;
}

.store-info{
text-align:center;
color:#777;
font-size:14px;
margin:5px 0;
}

.status{
background:#000;
color:#fff;
text-align:center;
padding:10px;
border-radius:12px;
font-size:14px;
margin-top:10px;
}

.delivery{
display:inline-block;
background:#e9f7ef;
color:#1e7e34;
padding:8px 14px;
border-radius:12px;
font-size:13px;
font-weight:600;
margin-top:12px;
}

/* CATEGORIAS */
.section{
padding:20px;
}

.section h2{
font-size:18px;
margin-bottom:15px;
}

.product-card{
display:flex;
background:#fff;
margin-bottom:15px;
border-radius:15px;
overflow:hidden;
box-shadow:0 2px 10px rgba(0,0,0,0.05);
cursor:pointer;
transition:0.2s;
}

.product-card:hover{
transform:scale(1.02);
}

.product-card img{
width:110px;
height:110px;
object-fit:cover;
}

.product-info{
padding:10px;
flex:1;
}

.product-info h3{
font-size:15px;
margin-bottom:5px;
}

.product-info p{
font-size:13px;
color:#666;
margin-bottom:8px;
}

.price{
font-weight:600;
color:#000;
}

/* BOTÃO CARRINHO */
.cart-button{
position:fixed;
bottom:20px;
right:20px;
background:#ea1d2c;
color:#fff;
border:none;
padding:15px 20px;
border-radius:50px;
font-weight:600;
box-shadow:0 5px 20px rgba(0,0,0,0.2);
cursor:pointer;
z-index:999;
}
</style>
</head>

<body>

<div class="header"></div>

<div class="store-card">
<div class="store-logo"></div>
<div class="store-name">Cantinho do Sabor</div>
<div class="store-info">⭐ 4,8 (28 avaliações) • 0,0 km</div>
<div class="status">Loja aberta • Entrega grátis</div>
<div style="text-align:center;">
<div class="delivery">🚚 Entrega grátis</div>
</div>
</div>

<!-- ========================= -->
<!-- CATEGORIAS COMEÇAM AQUI -->
<!-- ========================= -->

<div class="section">
<h2>Combos Promocionais!</h2>

<div class="product-card" onclick="addToCart('Dueto Tradicional',22.50)">
<img src="https://i.pinimg.com/736x/c6/44/0a/c6440adee5ef7fa7d38f1e6e44f28be5.jpg">
<div class="product-info">
<h3>Dueto Tradicional</h3>
<p>2 Pastéis de 1 Recheio (Carne, Mussarela ou Coalho e Frango)</p>
<div class="price">R$ 22,50</div>
</div>
</div>

</div>

<div class="section">
<h2>Batidinhas de Açaí Gourmet!</h2>

<div class="product-card" onclick="addToCart('Açaí 300ml',14.90)">
<img src="https://i.pinimg.com/736x/cf/3e/ce/cf3eced59ad15ee6fc1ffb3ebe057cd6.jpg">
<div class="product-info">
<h3>300ml - 1 Unidade</h3>
<p>Batidinha de Açaí Gourmet</p>
<div class="price">R$ 14,90</div>
</div>
</div>

</div>
<!-- ========================= -->
<!-- CLÁSSICOS INESQUECÍVEIS -->
<!-- ========================= -->

<div class="section">
<h2>Clássicos Inesquecíveis!</h2>

<div class="product-card" onclick="addToCart('Caipira Especial',17.50)">
<img src="https://i.pinimg.com/736x/54/f3/3e/54f33e374276eb01904b8a7bfe94081e.jpg">
<div class="product-info">
<h3>Caipira Especial</h3>
<p>Frango com Milho</p>
<div class="price">R$ 17,50</div>
</div>
</div>

<div class="product-card" onclick="addToCart('O Queridinho',17.50)">
<img src="https://i.pinimg.com/736x/0e/ba/e1/0ebae10f386aaf02dda228b58951ce41.jpg">
<div class="product-info">
<h3>O Queridinho</h3>
<p>Carne com Queijo</p>
<div class="price">R$ 17,50</div>
</div>
</div>

<div class="product-card" onclick="addToCart('Super Cremoso',18.50)">
<img src="https://i.pinimg.com/736x/66/20/80/662080576d5755f1fb79d243117a37d8.jpg">
<div class="product-info">
<h3>Super Cremoso</h3>
<p>Frango com Requeijão</p>
<div class="price">R$ 18,50</div>
</div>
</div>

</div>


<!-- ========================= -->
<!-- MONTE SEU PASTEL -->
<!-- ========================= -->

<div class="section">
<h2>Monte o Seu Pastel Crocante!</h2>

<div class="product-card" onclick="openCustom('Pastel 2 Recheios',17.50,2)">
<img src="https://i.pinimg.com/736x/01/4e/04/014e04188feecfd5ea2ac209eb3ad09b.jpg">
<div class="product-info">
<h3>2 Recheios</h3>
<div class="price">R$ 17,50</div>
</div>
</div>

<div class="product-card" onclick="openCustom('Pastel 3 Recheios',19.50,3)">
<img src="https://i.pinimg.com/736x/01/4e/04/014e04188feecfd5ea2ac209eb3ad09b.jpg">
<div class="product-info">
<h3>3 Recheios</h3>
<div class="price">R$ 19,50</div>
</div>
</div>

<div class="product-card" onclick="openCustom('Pastel 4 Recheios',21.50,4)">
<img src="https://i.pinimg.com/736x/01/4e/04/014e04188feecfd5ea2ac209eb3ad09b.jpg">
<div class="product-info">
<h3>4 Recheios</h3>
<div class="price">R$ 21,50</div>
</div>
</div>

</div>


<!-- ========================= -->
<!-- MONTE SEU CUSCUZ -->
<!-- ========================= -->

<div class="section">
<h2>Monte o Seu Cuscuz Recheado!</h2>

<div class="product-card" onclick="openCustom('Cuscuz 2 Recheios',16.50,2)">
<img src="https://i.pinimg.com/736x/b7/a1/a8/b7a1a8f4f27068bf9ab780cf38434bb0.jpg">
<div class="product-info">
<h3>2 Recheios</h3>
<div class="price">R$ 16,50</div>
</div>
</div>

<div class="product-card" onclick="openCustom('Cuscuz 3 Recheios',18.50,3)">
<img src="https://i.pinimg.com/736x/b7/a1/a8/b7a1a8f4f27068bf9ab780cf38434bb0.jpg">
<div class="product-info">
<h3>3 Recheios</h3>
<div class="price">R$ 18,50</div>
</div>
</div>

<div class="product-card" onclick="openCustom('Cuscuz 4 Recheios',20.50,4)">
<img src="https://i.pinimg.com/736x/b7/a1/a8/b7a1a8f4f27068bf9ab780cf38434bb0.jpg">
<div class="product-info">
<h3>4 Recheios</h3>
<div class="price">R$ 20,50</div>
</div>
</div>

</div>


<!-- ========================= -->
<!-- MONTE SUA TAPIOCA -->
<!-- ========================= -->

<div class="section">
<h2>Monte a Sua Tapioca Recheada!</h2>

<div class="product-card" onclick="openCustom('Tapioca 2 Recheios',17,2)">
<img src="https://i.pinimg.com/736x/23/45/4a/23454a1e2d9d8885839c89a71cd90cbf.jpg">
<div class="product-info">
<h3>2 Recheios</h3>
<div class="price">R$ 17,00</div>
</div>
</div>

<div class="product-card" onclick="openCustom('Tapioca 3 Recheios',19,3)">
<img src="https://i.pinimg.com/736x/23/45/4a/23454a1e2d9d8885839c89a71cd90cbf.jpg">
<div class="product-info">
<h3>3 Recheios</h3>
<div class="price">R$ 19,00</div>
</div>
</div>

<div class="product-card" onclick="openCustom('Tapioca 4 Recheios',21,4)">
<img src="https://i.pinimg.com/736x/23/45/4a/23454a1e2d9d8885839c89a71cd90cbf.jpg">
<div class="product-info">
<h3>4 Recheios</h3>
<div class="price">R$ 21,00</div>
</div>
</div>

</div>


<!-- ========================= -->
<!-- NOVIDADES -->
<!-- ========================= -->

<div class="section">
<h2>Novidade Especiais!</h2>

<div class="product-card" onclick="addToCart('Mini Pastéis Pernambucanos',16.50)">
<img src="https://i.ytimg.com/vi/03C8mGqozSw/hq720.jpg">
<div class="product-info">
<h3>Mini Pastéis Pernambucanos</h3>
<p>Carne polvilhados com açúcar e canela</p>
<div class="price">R$ 16,50</div>
</div>
</div>

</div>


<!-- ========================= -->
<!-- CARRINHO -->
<!-- ========================= -->

<button class="cart-button" onclick="openCart()">🛒 Ver Carrinho</button>

<div id="cartModal" style="display:none; position:fixed; bottom:0; left:0; right:0; background:white; height:80%; border-radius:25px 25px 0 0; padding:20px; overflow:auto; z-index:1000;">
<h2>Seu Pedido</h2>
<div id="cartItems"></div>
<h3 id="cartTotal" style="margin-top:15px;"></h3>

<input type="text" id="nome" placeholder="Seu nome" style="width:100%;padding:10px;margin-top:10px;">
<input type="text" id="endereco" placeholder="Seu endereço" style="width:100%;padding:10px;margin-top:10px;">

<select id="pagamento" style="width:100%;padding:10px;margin-top:10px;">
<option>Dinheiro</option>
<option>Pix</option>
<option>Cartão na Entrega</option>
</select>

<button onclick="sendWhats()" style="margin-top:15px;width:100%;padding:15px;background:#25d366;color:white;border:none;border-radius:10px;font-weight:600;">
Finalizar no WhatsApp
</button>

<button onclick="closeCart()" style="margin-top:10px;width:100%;padding:10px;background:#ccc;border:none;border-radius:10px;">
Fechar
</button>
</div>
<!-- ========================= -->
<!-- MODAL PERSONALIZAÇÃO -->
<!-- ========================= -->

<div id="customModal" style="display:none; position:fixed; inset:0; background:rgba(0,0,0,0.6); z-index:2000; align-items:center; justify-content:center;">
<div style="background:white; width:90%; max-height:90%; overflow:auto; border-radius:20px; padding:20px;">

<h2 id="customTitle"></h2>
<p id="customPrice"></p>

<h3>Escolha seus Recheios</h3>
<div id="recheios"></div>

<button onclick="confirmCustom()" style="margin-top:15px;width:100%;padding:12px;background:#ea1d2c;color:white;border:none;border-radius:10px;font-weight:600;">
Adicionar ao Carrinho
</button>

<button onclick="closeCustom()" style="margin-top:10px;width:100%;padding:10px;background:#ccc;border:none;border-radius:10px;">
Cancelar
</button>

</div>
</div>

<script>

let cart = [];
let currentItem = {};
let maxRecheios = 0;

const listaRecheios = [
"Frango","Carne","Pernil","Salsicha","Mussarela",
"Coalho","Milho","Azeitona","Cream Cheese",
"Requeijão","Cheddar","Catupiry","Alho Frito","Pimenta Calabresa"
];

function addToCart(nome, preco){
cart.push({nome, preco});
updateCart();
alert("Adicionado ao carrinho!");
}

function openCustom(nome, preco, limite){
currentItem = {nome, preco};
maxRecheios = limite;

document.getElementById("customTitle").innerText = nome;
document.getElementById("customPrice").innerText = "R$ " + preco.toFixed(2);

let html = "";
listaRecheios.forEach(r=>{
html += `
<label style="display:block;margin:5px 0;">
<input type="checkbox" value="${r}" onchange="validarRecheios()"> ${r}
</label>`;
});

document.getElementById("recheios").innerHTML = html;
document.getElementById("customModal").style.display = "flex";
}

function validarRecheios(){
let checkboxes = document.querySelectorAll('#recheios input:checked');
if(checkboxes.length > maxRecheios){
alert("Você só pode escolher até "+maxRecheios+" recheios");
checkboxes[checkboxes.length-1].checked = false;
}
}

function confirmCustom(){
let selecionados = document.querySelectorAll('#recheios input:checked');
if(selecionados.length !== maxRecheios){
alert("Escolha exatamente "+maxRecheios+" recheios");
return;
}

let recheiosEscolhidos = [];
selecionados.forEach(c=> recheiosEscolhidos.push(c.value));

cart.push({
nome: currentItem.nome + " ("+recheiosEscolhidos.join(", ")+")",
preco: currentItem.preco
});

closeCustom();
updateCart();
alert("Adicionado ao carrinho!");
}

function closeCustom(){
document.getElementById("customModal").style.display = "none";
}

function openCart(){
document.getElementById("cartModal").style.display = "block";
}

function closeCart(){
document.getElementById("cartModal").style.display = "none";
}

function updateCart(){
let container = document.getElementById("cartItems");
container.innerHTML = "";

let total = 0;

cart.forEach((item,index)=>{
total += item.preco;
container.innerHTML += `
<div style="display:flex;justify-content:space-between;margin:8px 0;">
<span>${item.nome}</span>
<span>R$ ${item.preco.toFixed(2)}</span>
</div>
`;
});

document.getElementById("cartTotal").innerText = "Total: R$ "+ total.toFixed(2);
}

function sendWhats(){

if(cart.length === 0){
alert("Seu carrinho está vazio!");
return;
}

let nome = document.getElementById("nome").value;
let endereco = document.getElementById("endereco").value;
let pagamento = document.getElementById("pagamento").value;

if(!nome || !endereco){
alert("Preencha nome e endereço");
return;
}

let total = 0;
let mensagem = "*NOVO PEDIDO*%0A%0A";

cart.forEach(item=>{
mensagem += "- "+item.nome+" - R$ "+item.preco.toFixed(2)+"%0A";
total += item.preco;
});

mensagem += "%0ATotal: R$ "+total.toFixed(2);
mensagem += "%0AEntrega: Grátis";
mensagem += "%0A%0ANome: "+nome;
mensagem += "%0AEndereço: "+endereco;
mensagem += "%0APagamento: "+pagamento;

window.open("https://wa.me/5587933009283?text="+mensagem, "_blank");
}

</script>

</body>
</html>
