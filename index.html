<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cantinho do Sabor</title>

<style>
*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:Arial, Helvetica, sans-serif;
}

body{
background:#f2f2f2;
padding-bottom:130px;
}

/* HEADER */

.header{
background:#fff;
padding:15px;
display:flex;
align-items:center;
gap:15px;
box-shadow:0 2px 6px rgba(0,0,0,0.05);
position:sticky;
top:0;
z-index:1000;
}

.logo{
width:70px;
height:70px;
border-radius:50%;
overflow:hidden;
}

.logo img{
width:100%;
height:100%;
object-fit:cover;
}

.loja-info h1{
font-size:18px;
font-weight:700;
}

.loja-info span{
color:green;
font-size:14px;
font-weight:600;
}

/* CATEGORIAS */

.categorias{
display:flex;
overflow-x:auto;
gap:10px;
padding:12px;
background:#fff;
position:sticky;
top:100px;
z-index:900;
}

.categorias button{
background:#eee;
border:none;
padding:8px 14px;
border-radius:20px;
cursor:pointer;
white-space:nowrap;
font-size:13px;
}

.categorias button.ativo{
background:#ea1d2c;
color:#fff;
}

/* PRODUTOS */

.section{
padding:15px;
}

.card{
background:#fff;
padding:15px;
border-radius:14px;
margin-bottom:12px;
display:flex;
justify-content:space-between;
align-items:center;
box-shadow:0 2px 6px rgba(0,0,0,0.04);
}

.card-info h3{
font-size:15px;
margin-bottom:5px;
}

.card-info p{
font-size:12px;
color:#777;
}

.card-info strong{
color:#ea1d2c;
font-size:14px;
}

.card button{
background:#ea1d2c;
border:none;
color:#fff;
padding:8px 14px;
border-radius:20px;
cursor:pointer;
font-size:13px;
}

/* CARRINHO FIXO */

.carrinho{
position:fixed;
bottom:0;
left:0;
right:0;
background:#fff;
padding:15px;
box-shadow:0 -3px 10px rgba(0,0,0,0.08);
}

.carrinho-top{
display:flex;
justify-content:space-between;
margin-bottom:8px;
font-weight:600;
}

.carrinho button{
width:100%;
background:#ea1d2c;
color:#fff;
border:none;
padding:12px;
border-radius:10px;
font-size:15px;
cursor:pointer;
}

/* MODAL GLOBAL */

.modal{
display:none;
position:fixed;
inset:0;
background:rgba(0,0,0,0.5);
z-index:2000;
align-items:center;
justify-content:center;
}

.modal-content{
background:#fff;
width:95%;
max-width:420px;
border-radius:20px;
padding:20px;
max-height:90%;
overflow:auto;
}

/* BOTÕES OPÇÃO */

.opcoes{
display:grid;
grid-template-columns:1fr 1fr;
gap:8px;
margin-top:8px;
}

.opcao{
padding:8px;
border:2px solid #ddd;
border-radius:10px;
text-align:center;
font-size:13px;
cursor:pointer;
}

.opcao.ativo{
border-color:#ea1d2c;
background:#fff3f4;
color:#ea1d2c;
font-weight:600;
}

/* QUANTIDADE */

.qtd-box{
display:flex;
align-items:center;
gap:6px;
}

.qtd-box button{
background:#ea1d2c;
color:#fff;
border:none;
padding:3px 7px;
border-radius:5px;
}

.checkout-resumo{
margin-bottom:15px;
font-size:14px;
}
</style>
</head>

<body>

<div class="header">
<div class="logo">
<img src="https://i.pinimg.com/736x/15/ac/c8/15acc8b00600f7f49f899cccbb55050d.jpg">
</div>
<div class="loja-info">
<h1>Delivery Crocante</h1>
<span>Entrega grátis</span>
</div>
</div>

<div class="categorias" id="categorias"></div>

<div class="section" id="produtos"></div>

<div class="carrinho">
<div class="carrinho-top">
<span id="cartQtd">0 itens</span>
<span id="cartTotal">R$ 0,00</span>
</div>
<button onclick="abrirCheckout()">Ver Pedido</button>
</div>

<div class="modal" id="modalGlobal"></div>

<script>
  /* ================================
   BANCO DE DADOS ESTRUTURADO
================================ */

const DB = {

categorias: [
"Combos Promocionais!",
"Monte o Seu Pastel Crocante!",
"Monte o Seu Cuscuz Recheado!",
"Monte a Sua Tapioca Recheada!",
"Batidinhas de Açaí Gourmet!",
"Clássicos Inesquecíveis!",
"Novidade Especiais!"
],

produtos: [

{
id:"dueto",
categoria:"Combos Promocionais!",
nome:"Dueto Tradicional",
descricao:"2 pastéis tradicionais com sabores à escolha",
preco:22.50,
tipo:"dueto"
},

{
id:"pastel",
categoria:"Monte o Seu Pastel Crocante!",
nome:"Monte o Seu Pastel",
descricao:"Escolha exatamente 3 recheios",
preco:19.50,
tipo:"personalizavel"
}

],

recheios:["Frango","Carne","Mussarela","Coalho","Calabresa","Catupiry","Milho","Bacon"],

acompanhamentos:[
{nome:"Batata P",preco:6},
{nome:"Batata M",preco:8},
{nome:"Bolinha P",preco:5},
{nome:"Mini Pastel P",preco:7}
],

bebidas:[
{nome:"Morango",preco300:9,preco500:14},
{nome:"Maracujá",preco300:9,preco500:14},
{nome:"Abacaxi",preco300:9,preco500:14}
]

};


/* ================================
   VARIÁVEIS GLOBAIS
================================ */

let categoriaAtiva = DB.categorias[0];
let carrinho = JSON.parse(localStorage.getItem("carrinho")) || [];


/* ================================
   RENDER CATEGORIAS
================================ */

function renderCategorias(){

let container = document.getElementById("categorias");
container.innerHTML = "";

DB.categorias.forEach(cat=>{

let btn = document.createElement("button");
btn.innerText = cat;

if(cat === categoriaAtiva){
btn.classList.add("ativo");
}

btn.onclick = function(){
categoriaAtiva = cat;
renderCategorias();
renderProdutos();
};

container.appendChild(btn);

});

}


/* ================================
   RENDER PRODUTOS
================================ */

function renderProdutos(){

let container = document.getElementById("produtos");
container.innerHTML = "";

let filtrados = DB.produtos.filter(p=>p.categoria === categoriaAtiva);

filtrados.forEach(prod=>{

container.innerHTML += `
<div class="card">
<div class="card-info">
<h3>${prod.nome}</h3>
<p>${prod.descricao}</p>
<strong>R$ ${prod.preco.toFixed(2)}</strong>
</div>
<button onclick="abrirProduto('${prod.id}')">Adicionar</button>
</div>
`;

});

}


/* ================================
   CARRINHO
================================ */

function salvarCarrinho(){
localStorage.setItem("carrinho", JSON.stringify(carrinho));
}

function atualizarCarrinhoUI(){

let total = 0;
let qtd = 0;

carrinho.forEach(item=>{
total += item.preco * item.quantidade;
qtd += item.quantidade;
});

document.getElementById("cartTotal").innerText = "R$ "+total.toFixed(2);
document.getElementById("cartQtd").innerText = qtd+" itens";

salvarCarrinho();
}

function gerarHash(item){
return JSON.stringify(item);
}

function adicionarAoCarrinho(item){

let hash = gerarHash(item);

let existente = carrinho.find(p=>p.hash === hash);

if(existente){
existente.quantidade++;
}else{
carrinho.push({
...item,
quantidade:1,
hash
});
}

atualizarCarrinhoUI();
}


/* ================================
   CHECKOUT
================================ */

function abrirCheckout(){

if(carrinho.length === 0){
alert("Carrinho vazio");
return;
}

let total = carrinho.reduce((acc,item)=>acc+(item.preco*item.quantidade),0);

let resumo = `
<div class="modal-content">
<h3>Seu Pedido</h3>
<div class="checkout-resumo">
`;

carrinho.forEach(item=>{
resumo += `
<div style="margin-bottom:8px;">
<strong>${item.nome}</strong><br>
Qtd: ${item.quantidade}<br>
R$ ${(item.preco*item.quantidade).toFixed(2)}
</div>
`;
});

resumo += `
<hr style="margin:10px 0;">
<strong>Total: R$ ${total.toFixed(2)}</strong>
</div>

<button onclick="enviarWhatsApp()" 
style="width:100%;background:#ea1d2c;color:white;border:none;padding:12px;border-radius:10px;">
Enviar Pedido
</button>

<button onclick="fecharModal()" 
style="margin-top:8px;width:100%;background:#ddd;border:none;padding:10px;border-radius:10px;">
Fechar
</button>

</div>
`;

abrirModal(resumo);
}

function enviarWhatsApp(){

let mensagem="Olá, gostaria de pedir:%0A%0A";

carrinho.forEach(item=>{
mensagem += `- ${item.nome} x${item.quantidade}%0A`;
});

let total = carrinho.reduce((acc,item)=>acc+(item.preco*item.quantidade),0);

mensagem += `%0ATotal: R$ ${total.toFixed(2)}`;

window.open(`https://wa.me/5587933009283?text=${mensagem}`);

}


/* ================================
   MODAL GLOBAL
================================ */

function abrirModal(conteudo){

let modal = document.getElementById("modalGlobal");
modal.innerHTML = conteudo;
modal.style.display="flex";

modal.onclick = function(e){
if(e.target.id === "modalGlobal"){
fecharModal();
}
};

}

function fecharModal(){
document.getElementById("modalGlobal").style.display="none";
}


/* ================================
   INICIALIZAÇÃO
================================ */

renderCategorias();
renderProdutos();
atualizarCarrinhoUI();
  /* =====================================
   ABRIR PRODUTO
===================================== */

function abrirProduto(id){

let produto = DB.produtos.find(p=>p.id===id);

if(produto.tipo === "dueto"){
abrirDueto(produto);
}

if(produto.tipo === "personalizavel"){
abrirPastel(produto);
}

}


/* =====================================
   DUETO TRADICIONAL
===================================== */

function abrirDueto(produto){

let selecao = {p1:null,p2:null};

let html = `
<div class="modal-content">
<h3>${produto.nome}</h3>

<h4>Escolha o 1º Pastel</h4>
<div class="opcoes" id="dueto1"></div>

<h4 style="margin-top:10px;">Escolha o 2º Pastel</h4>
<div class="opcoes" id="dueto2"></div>

<button id="btnDueto" 
style="margin-top:15px;width:100%;background:#ea1d2c;color:white;border:none;padding:12px;border-radius:10px;">
Adicionar • R$ ${produto.preco.toFixed(2)}
</button>
</div>
`;

abrirModal(html);

function renderOpcoes(idCampo,numero){

let container = document.getElementById(idCampo);

DB.recheios.slice(0,4).forEach(sabor=>{

let div = document.createElement("div");
div.className="opcao";
div.innerText=sabor;

div.onclick=function(){

if(numero===1){ selecao.p1=sabor; }
else{ selecao.p2=sabor; }

[...container.children].forEach(el=>el.classList.remove("ativo"));
div.classList.add("ativo");
};

container.appendChild(div);

});
}

renderOpcoes("dueto1",1);
renderOpcoes("dueto2",2);

document.getElementById("btnDueto").onclick=function(){

if(!selecao.p1 || !selecao.p2){
alert("Escolha os dois pastéis.");
return;
}

let item = {
nome:`Dueto (${selecao.p1} + ${selecao.p2})`,
preco:produto.preco,
detalhes:{
pastel1:selecao.p1,
pastel2:selecao.p2
}
};

adicionarAoCarrinho(item);
fecharModal();

};

}


/* =====================================
   MONTE SEU PASTEL
===================================== */

function abrirPastel(produto){

let selecao = {
recheios:[],
acompanhamentos:{},
bebidas:[]
};

let total = produto.preco;

let html = `
<div class="modal-content">
<h3>${produto.nome}</h3>
<p style="font-size:13px;color:#666;">Escolha exatamente 3 recheios</p>

<h4>Recheios</h4>
<div class="opcoes" id="recheiosBox"></div>

<h4 style="margin-top:10px;">Acompanhamentos</h4>
<div id="acompBox"></div>

<h4 style="margin-top:10px;">Batidas e Drinks</h4>
<div id="bebidasBox"></div>

<h3 id="subtotalBox">Total: R$ ${total.toFixed(2)}</h3>

<button id="btnPastel"
style="margin-top:10px;width:100%;background:#ea1d2c;color:white;border:none;padding:12px;border-radius:10px;">
Adicionar ao Carrinho
</button>
</div>
`;

abrirModal(html);


/* RECHEIOS */

let recheiosBox = document.getElementById("recheiosBox");

DB.recheios.forEach(r=>{

let div = document.createElement("div");
div.className="opcao";
div.innerText=r;

div.onclick=function(){

if(selecao.recheios.includes(r)){
selecao.recheios = selecao.recheios.filter(x=>x!==r);
div.classList.remove("ativo");
}else{

if(selecao.recheios.length>=3){
alert("Máximo 3 recheios.");
return;
}

selecao.recheios.push(r);
div.classList.add("ativo");
}

};

recheiosBox.appendChild(div);

});


/* ACOMPANHAMENTOS */

let acompBox = document.getElementById("acompBox");

DB.acompanhamentos.forEach(a=>{

let linha = document.createElement("div");

linha.innerHTML=`
<div style="display:flex;justify-content:space-between;margin-bottom:5px;">
<span>${a.nome} - R$ ${a.preco}</span>
<div class="qtd-box">
<button>-</button>
<span>0</span>
<button>+</button>
</div>
</div>
`;

let btnMenos = linha.querySelectorAll("button")[0];
let spanQtd = linha.querySelector("span:nth-child(2)");
let btnMais = linha.querySelectorAll("button")[1];

btnMais.onclick=function(){
if(!selecao.acompanhamentos[a.nome]) selecao.acompanhamentos[a.nome]=0;
selecao.acompanhamentos[a.nome]++;
atualizarSubtotal();
};

btnMenos.onclick=function(){
if(selecao.acompanhamentos[a.nome]){
selecao.acompanhamentos[a.nome]--;
if(selecao.acompanhamentos[a.nome]<=0){
delete selecao.acompanhamentos[a.nome];
}
atualizarSubtotal();
}
};

function atualizarSubtotal(){

total = produto.preco;

Object.keys(selecao.acompanhamentos).forEach(nome=>{
let qtd = selecao.acompanhamentos[nome];
let precoItem = DB.acompanhamentos.find(x=>x.nome===nome).preco;
total += qtd * precoItem;
});

selecao.bebidas.forEach(b=> total+=b.preco);

document.getElementById("subtotalBox").innerText="Total: R$ "+total.toFixed(2);
spanQtd.innerText = selecao.acompanhamentos[a.nome] || 0;
}

acompBox.appendChild(linha);

});


/* BEBIDAS */

let bebidasBox = document.getElementById("bebidasBox");

DB.bebidas.forEach(b=>{

let div = document.createElement("div");

div.innerHTML=`
<div style="margin-bottom:6px;">
<strong>${b.nome}</strong><br>
300ml R$ ${b.preco300}
<button>+</button>
&nbsp;&nbsp;
500ml R$ ${b.preco500}
<button>+</button>
</div>
`;

let btn300 = div.querySelectorAll("button")[0];
let btn500 = div.querySelectorAll("button")[1];

btn300.onclick=function(){
selecao.bebidas.push({nome:b.nome,tamanho:300,preco:b.preco300});
atualizarSubtotal();
};

btn500.onclick=function(){
selecao.bebidas.push({nome:b.nome,tamanho:500,preco:b.preco500+5});
atualizarSubtotal();
};

bebidasBox.appendChild(div);

});


/* CONFIRMAR */

document.getElementById("btnPastel").onclick=function(){

if(selecao.recheios.length!==3){
alert("Escolha exatamente 3 recheios.");
return;
}

let item = {
nome:`Pastel (${selecao.recheios.join(", ")})`,
preco:total,
detalhes:selecao
};

adicionarAoCarrinho(item);
fecharModal();

};

  }
