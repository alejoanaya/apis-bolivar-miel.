<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Apis Bolívar - Miel Natural</title>
<style>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 20px;
  background: url('fondo.jpg') no-repeat center center fixed;
  background-size: cover;
}

.contenedor {
  max-width: 800px;
  margin: auto;
  background: rgba(255,255,255,0.95);
  padding: 25px;
  border-radius: 20px;
  box-shadow: 0 0 20px rgba(0,0,0,0.2);
  animation: fadeIn 1s ease;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px);}
  to { opacity: 1; transform: translateY(0);}
}

.img-miel {
  width: 55%;
  max-width: 280px;
  display: block;
  margin: auto;
  border-radius: 15px;
  animation: floatMove 2s ease-in-out infinite alternate;
}

@keyframes floatMove {
  0% { transform: translateY(0px);}
  50% { transform: translateY(-15px);}
  100% { transform: translateY(0px);}
}

input, select {
  width: 100%;
  padding: 12px;
  margin-top: 5px;
  border-radius: 10px;
  border: 1px solid #aaa;
  font-size: 16px;
}

button {
  width: 100%;
  padding: 14px;
  margin-top: 15px;
  border-radius: 10px;
  border: none;
  background: #f4a300;
  color: white;
  font-size: 18px;
  font-weight: bold;
  cursor: pointer;
  transition: 0.3s;
}

button:hover { background: #d98a00;}

.error-msg {
  color: red;
  font-size: 16px;
  margin-top: 5px;
  text-align: center;
}

.beneficios {
  background: #fff3cd;
  padding: 15px;
  border-radius: 12px;
  margin: 15px 0;
  border-left: 5px solid #f4a300;
}

.confirmacion {
  display: none;
  background: #d1ecf1;
  border: 2px solid #0c5460;
  color: #0c5460;
  padding: 20px;
  border-radius: 15px;
  text-align: center;
  font-size: 18px;
  position: relative;
  animation: fadeIn 0.5s ease;
}

.confirmacion .cerrar {
  position: absolute;
  top: 5px;
  right: 10px;
  cursor: pointer;
  font-weight: bold;
  font-size: 20px;
}

h1 {
  text-align:center;
  color: #d98a00;
  animation: titleFade 1s ease;
}

@keyframes titleFade {
  from { opacity: 0; transform: scale(0.8);}
  to { opacity: 1; transform: scale(1);}
}
</style>
</head>
<body>

<h1>Apis Bolívar – Miel 100% Natural</h1>

<div class="contenedor">

  <!-- Imagen del producto -->
  <img src="miel.jpg" class="img-miel" />

  <div class="beneficios">
    <h3>🌿 Beneficios de la miel</h3>
    <ul>
      <li>Fortalece el sistema inmunológico.</li>
      <li>Mejora la digestión.</li>
      <li>Alivia dolores de garganta.</li>
      <li>Aporta energía natural.</li>
      <li>Contiene antioxidantes.</li>
    </ul>
    <h3>✨ Usos recomendados</h3>
    <ul>
      <li>Endulzar bebidas de forma natural.</li>
      <li>Aplicar en mascarillas faciales.</li>
      <li>Consumir en ayunas para energía.</li>
      <li>Perfecta para recetas y postres.</li>
    </ul>
  </div>

  <h2>🔥 Promoción especial</h2>
  <p><b>Precio normal:</b> $28.000 COP</p>
  <p style="font-size:20px; font-weight:bold; color:#d98a00;">✨ Llévate 2 frascos por <u>$56.000 COP</u></p>

  <h3>Datos del pedido</h3>
  <label>Nombre completo</label>
  <input id="nombre" />
  <div id="err-nombre" class="error-msg"></div>

  <label>Dirección</label>
  <input id="direccion" placeholder="Ej: Cali, Km 18, Dagua..." />
  <div id="err-direccion" class="error-msg"></div>

  <label>Teléfono</label>
  <input id="telefono" />
  <div id="err-telefono" class="error-msg"></div>

  <label>Cantidad</label>
  <input type="number" id="cantidad" />
  <div id="err-cantidad" class="error-msg"></div>

  <button onclick="enviarPedido()">Enviar pedido</button>

  <p style="text-align:center; margin-top:10px; color:#555;">Se reciben pagos con nequi o contra entrega.</p>

  <div id="confirmacion" class="confirmacion">
    <span class="cerrar" onclick="cerrarConfirmacion()">×</span>
    ¡Gracias por tu compra! Serás redireccionado al vendedor.
  </div>

</div>

<script>
function limpiarErrores(){
  document.getElementById("err-nombre").innerHTML = "";
  document.getElementById("err-direccion").innerHTML = "";
  document.getElementById("err-telefono").innerHTML = "";
  document.getElementById("err-cantidad").innerHTML = "";
}

function enviarPedido() {
  limpiarErrores();

  let n = document.getElementById("nombre").value;
  let d = document.getElementById("direccion").value;
  let t = document.getElementById("telefono").value;
  let c = document.getElementById("cantidad").value;

  let valido = true;

  if (!n) { document.getElementById("err-nombre").innerHTML = "Por favor ingresa tu nombre"; valido = false; }
  if (!d) { document.getElementById("err-direccion").innerHTML = "Por favor ingresa tu dirección"; valido = false; }
  if (!t) { document.getElementById("err-telefono").innerHTML = "Por favor ingresa tu teléfono"; valido = false; }
  if (!c) { document.getElementById("err-cantidad").innerHTML = "Por favor ingresa la cantidad"; valido = false; }

  if (!valido) return;

  let confirmBox = document.getElementById("confirmacion");
  confirmBox.style.display = "block";

  setTimeout(function(){
    let msg = `Nuevo pedido de miel:\nNombre: ${n}\nDirección: ${d}\nTeléfono: ${t}\nCantidad: ${c} frascos`;
    window.location.href = `https://wa.me/573164407273?text=${encodeURIComponent(msg)}`;
  }, 2000);
}

function cerrarConfirmacion(){
  document.getElementById("confirmacion").style.display = "none";
}
</script>
</body>
</html>
