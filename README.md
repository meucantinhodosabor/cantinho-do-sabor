<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cantinho do Sabor</title>

<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">

<style>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Inter', sans-serif;
  background: #f4f4f4;
  color: #222;
}

/* CAPA TOPO */

.capa {
  position: relative;
  width: 100%;
  height: 200px;
  background: url('https://i.pinimg.com/736x/c6/44/0a/c6440adee5ef7fa7d38f1e6e44f28be5.jpg') center/cover no-repeat;
}

/* LOGO REDONDA CENTRAL */

.logo-loja {
  position: absolute;
  bottom: -50px;
  left: 50%;
  transform: translateX(-50%);
  width: 110px;
  height: 110px;
  border-radius: 50%;
  border: 6px solid white;
  box-shadow: 0 8px 25px rgba(0,0,0,0.2);
  overflow: hidden;
  background: white;
}

.logo-loja img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* INFORMAÇÕES LOJA */

.info-loja {
  margin-top: 70px;
  text-align: center;
  padding: 0 20px;
}

.info-loja h1 {
  font-size: 22px;
  font-weight: 700;
}

.info-loja p {
  font-size: 14px;
  color: #666;
  margin-top: 5px;
}

/* CATEGORIAS */

.categoria {
  padding: 25px 20px 10px 20px;
}

.categoria h2 {
  font-size: 18px;
  font-weight: 600;
  margin-bottom: 15px;
}

/* CARD PRODUTO */

.produto {
  background: white;
  border-radius: 16px;
  margin-bottom: 15px;
  padding: 15px;
  display: flex;
  gap: 15px;
  box-shadow: 0 4px 15px rgba(0,0,0,0.06);
  transition: 0.2s ease;
}

.produto:hover {
  transform: translateY(-3px);
}

.produto img {
  width: 95px;
  height: 95px;
  border-radius: 12px;
  object-fit: cover;
}

.info {
  flex: 1;
}

.info h3 {
  font-size: 15px;
  font-weight: 600;
  margin-bottom: 5px;
}

.info p {
  font-size: 13px;
  color: #666;
}

.preco {
  font-weight: 700;
  margin-top: 6px;
  font-size: 14px;
}

/* BOTÃO FIXO */

.botao-pix {
  position: fixed;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  background: linear-gradient(135deg, #ff7a00, #ff3d00);
  color: white;
  border: none;
  padding: 14px 30px;
  border-radius: 50px;
  font-weight: 600;
  box-shadow: 0 8px 25px rgba(255,61,0,0.4);
  cursor: pointer;
}

/* MODAL PIX */

.modal-pix {
  display: none;
  position: fixed;
  z-index: 999;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.6);
}

.modal-content {
  background: white;
  margin: 20% auto;
  padding: 25px;
  width: 90%;
  max-width: 400px;
  border-radius: 18px;
  text-align: center;
  box-shadow: 0 15px 40px rgba(0,0,0,0.2);
}

.modal-content textarea {
  width: 100%;
  height: 80px;
  margin: 10px 0;
  padding: 10px;
  border-radius: 8px;
  border: 1px solid #ddd;
  resize: none;
}

.modal-content button {
  background: linear-gradient(135deg, #ff7a00, #ff3d00);
  color: white;
  border: none;
  padding: 12px 20px;
  border-radius: 10px;
  cursor: pointer;
  width: 100%;
  font-weight: 600;
}

.close {
  text-align: right;
  font-size: 20px;
  cursor: pointer;
}

</style>
</head>

<body>

<!-- CAPA -->
<div class="capa">
  <div class="logo-loja">
    <img src="https://i.pinimg.com/736x/15/ac/c8/15acc8b00600f7f49f899cccbb55050d.jpg">
  </div>
</div>

<!-- INFO LOJA -->
<div class="info-loja">
  <h1>Pastelaria & Açaí</h1>
  <p>Entrega grátis • 30-40 min • 4.9 ⭐</p>
</div>

<!-- COMBO DESTAQUE -->
<section class="categoria">
  <h2>🔥 Combo em Destaque</h2>

  <div class="produto">
    <img src="https://i.pinimg.com/736x/c6/44/0a/c6440adee5ef7fa7d38f1e6e44f28be5.jpg">
    <div class="info">
      <h3>Dueto Tradicional</h3>
      <p>2 Pastéis (Carne, Mussarela, Coalho ou Frango)</p>
      <div class="preco">R$ 22,50</div>
    </div>
  </div>
</section>

<button class="botao-pix" onclick="abrirModalPix()">Pagar com Pix</button>

<!-- MODAL PIX -->

<div id="modalPix" class="modal-pix">
  <div class="modal-content">
    <div class="close" onclick="fecharModalPix()">✕</div>
    <h2>Pagamento via Pix</h2>

    <textarea id="pixCode" readonly>
82e5f2e0-772e-46d6-8ec9-3dbcf9b2c54c
    </textarea>

    <button onclick="copiarPix()">Copiar Código Pix</button>
  </div>
</div>

<script>
function abrirModalPix() {
  document.getElementById("modalPix").style.display = "block";
}

function fecharModalPix() {
  document.getElementById("modalPix").style.display = "none";
}

function copiarPix() {
  const pix = document.getElementById("pixCode");
  navigator.clipboard.writeText(pix.value);
}
</script>

</body>
</html>
