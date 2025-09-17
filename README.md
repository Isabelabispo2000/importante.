<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Modo Secreto</title>
<style>
body{margin:0;padding:0;font-family:"Segoe UI",Arial,sans-serif;background:linear-gradient(to right,#b3f0e6,#ffe6e6);display:flex;justify-content:center;align-items:center;min-height:100vh;}
.senha-container{text-align:center;background:rgba(255,255,255,0.85);backdrop-filter:blur(8px);border-radius:20px;padding:40px 30px;box-shadow:0 8px 25px rgba(0,0,0,0.15);max-width:400px;width:90%;}
input[type="password"]{padding:12px;font-size:1rem;border-radius:10px;border:1px solid #ccc;width:100%;margin-top:10px;outline:none;}
button{margin-top:15px;padding:12px 25px;border:none;border-radius:20px;background-color:#1d6d50;color:white;font-size:1rem;cursor:pointer;transition:0.3s;}
button:hover{background-color:#14905d;}
#conteudoSecreto{display:none;width:100%;}
.card{background:rgba(255,255,255,0.95);backdrop-filter:blur(10px);border-radius:25px;box-shadow:0 10px 30px rgba(0,0,0,0.2);padding:50px 40px;max-width:750px;text-align:center;margin:40px auto;animation:fadeIn 0.7s ease-in-out;position:relative;}
.observacao{font-size:0.95rem;color:#777;margin-bottom:20px;font-style:italic;}
h1{font-size:1.6rem;margin:0 0 25px 0;font-weight:700;color:#333;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;}
p{font-size:1rem;margin:8px 0;line-height:1.5;color:#555;}
.buttons{margin-top:30px;display:flex;gap:15px;justify-content:center;flex-wrap:wrap;position:relative;height:80px;}
.btn-yes,.btn-no{padding:12px 22px;border-radius:30px;border:none;cursor:pointer;font-size:0.95rem;transition:all 0.3s ease;box-shadow:0 4px 8px rgba(0,0,0,0.15);max-width:280px;word-wrap:break-word;position:relative;}
.btn-yes{font-weight:bold;background:#fff;color:#1d6d50;}
.btn-yes:hover{background:#dfffe9;transform:scale(1.05);}
.btn-no{background:#fff;color:#8a1a1a;}
.btn-no:hover{background-color:#ffe3e3;transform:scale(1.05);}
@keyframes fadeIn{from{opacity:0;transform:translateY(15px);}to{opacity:1;transform:translateY(0);}}
.overlay{position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.4);display:none;justify-content:center;align-items:center;z-index:999;}
.popup{background:#fff;padding:30px 40px;border-radius:20px;text-align:center;max-width:500px;box-shadow:0 8px 25px rgba(0,0,0,0.3);animation:fadeIn 0.3s ease-in-out;}
.popup button{margin-top:20px;background-color:#1d6d50;color:white;border-radius:15px;padding:10px 20px;cursor:pointer;}
.popup button:hover{background-color:#14905d;}
.popup img{max-width:100%;border-radius:15px;}
</style>
</head>
<body>
<div class="senha-container" id="senhaContainer">
<h2>🕶️ Modo Secreto</h2>
<p>Para continuar digite a senha:</p>
<input type="password" id="senhaInput" placeholder="Digite a senha" autocapitalize="off" autocomplete="off" autocorrect="off">
<br>
<button id="btnEntrar">Entrar</button>
<p>Dica: nome da melhor aluna. Aceita maiúscula e minuscula.</p>
</div>

<div id="conteudoSecreto">
<div class="card">
<div class="observacao">Esse site contém um pouco de drama, mas isso é detalhe. Foca na resposta.</div>
<h1>TOP 10 MOTIVOS PARA VOLTAR A DAR AULA P/ T.I</h1>
<p>1. Sem uma instrutora mulher, minha representatividade caiu 50%. Agora sou minoria da minoria!</p>
<p>2. Vindo de humanas, estou tendo que fingir que entendo essa galera da tecnologia.</p>
<p>3. RH e ADM já estão se formando... já aprenderam tudo o que tinha pra aprender. Eles se viram.</p>
<p>4. Estou tendo que conviver com mais de 10 homens e nenhum deles é o homem que eu amo. Difícil</p>
<p>5. Por último e não menos importante: demorei pra desenvolver essa página (e daí que foi com o ChatGpt?)</p>
<p><b>Dito isso, você escolhe:</b></p>
<div class="buttons">
<button class="btn-yes" id="btnYes">Voltar a dar aula para T.I</button>
<button class="btn-no" id="btnNo">Continuar dando aula para os vizinhos, ignorando as observações citadas.</button>
</div>
</div>
</div>

<div class="overlay" id="overlay">
<div class="popup">
<div id="popupMensagem"></div>
<button onclick="fecharPopup()">Desculpa</button>
</div>
</div>

<script>
const senhaCorreta = "Isabela";
const inputSenha = document.getElementById("senhaInput");
const btnEntrar = document.getElementById("btnEntrar");

function verificarSenha() {
  inputSenha.blur(); // fecha teclado

  // Remove todos os espaços, tabs, quebras de linha e zero-width spaces
  let senha = inputSenha.value.replace(/[\s\u200B\r\n]+/g,"").toLowerCase();

  if(senha === senhaCorreta.toLowerCase()) {
    document.getElementById("senhaContainer").style.display = "none";
    document.getElementById("conteudoSecreto").style.display = "block";
  } else {
    alert("Senha incorreta! 😢 Tente novamente.");
    inputSenha.value="";
    inputSenha.focus();
  }
}

// Captura clique e toque
btnEntrar.addEventListener("click",verificarSenha);
btnEntrar.addEventListener("touchend",verificarSenha);

// Captura Enter no teclado
inputSenha.addEventListener("keydown",function(e){
  if(e.key==="Enter"){e.preventDefault();verificarSenha();}
});

// Popups
const btnNo=document.getElementById("btnNo");
const btnYes=document.getElementById("btnYes");
const overlay=document.getElementById("overlay");
const popupMensagem=document.getElementById("popupMensagem");
const mensagens=["Cada clique, uma lágrima!","Ok, vou tentar sobreviver sozinha na sala de TI...","Vou fingir que está tudo bem…","Isso dói mais que terminar um namoro..."];
let indiceMensagem=0;

function showPopup(msg){
  popupMensagem.innerText=msg;
  overlay.style.display="flex";
}
function showGif(){
  popupMensagem.innerHTML='<img src="https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExaDM4cXFmbmUzajF2dTgyaHNueG1hYzVmaHhnbHJ2dzkwdzRhcWFpMCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/5xtDarmwsuR9sDRObyU/giphy.gif" alt="GIF comemorativo" style="max-width:100%;border-radius:15px;">';
  overlay.querySelector("button").style.display="none";
  overlay.style.display="flex";
}

btnNo.addEventListener("click",()=>{showPopup(mensagens[indiceMensagem]);indiceMensagem=(indiceMensagem+1)%mensagens.length;});
btnNo.addEventListener("touchend",()=>{showPopup(mensagens[indiceMensagem]);indiceMensagem=(indiceMensagem+1)%mensagens.length;});
btnYes.addEventListener("click",showGif);
btnYes.addEventListener("touchend",showGif);

function fecharPopup(){
  overlay.style.display="none";
  overlay.querySelector("button").style.display="block";
}
</script>
</body>
</html>
