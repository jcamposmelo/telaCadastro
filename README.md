# telaCadastro
Tela de cadastro e login

1ª parte em JavaScript

```
let btn = document.querySelector("#verSenha");
let btnConfirm = document.querySelector("#verConfirmSenha");

let nome = document.querySelector("#nome");
let labelNome = document.querySelector("#labelNome");
let validNome = false;

let usuario = document.querySelector("#usuario");
let labelUsuario = document.querySelector("#labelUsuario");
let validUsuario = false;

let senha = document.querySelector("#senha");
let labelSenha = document.querySelector("#labelSenha");
let validSenha = false;

let confirmSenha = document.querySelector("#confirmSenha");
let labelConfirmSenha = document.querySelector("#labelConfirmSenha");
let validConfirmSenha = false;

let msgError = document.querySelector("#msgError");
let msgSuccess = document.querySelector("#msgSuccess");

nome.addEventListener("keyup", () => {
  if (nome.value.length <= 2) {
    labelNome.setAttribute("style", "color: red");
    labelNome.innerHTML = "Nome *Insira no minimo 3 caracteres";
    nome.setAttribute("style", "border-color: red");
    validNome = false;
  } else {
    labelNome.setAttribute("style", "color: green");
    labelNome.innerHTML = "Nome";
    nome.setAttribute("style", "border-color: green");
    validNome = true;
  }
});

usuario.addEventListener("keyup", () => {
  if (usuario.value.length <= 4) {
    labelUsuario.setAttribute("style", "color: red");
    labelUsuario.innerHTML = "Usuário *Insira no minimo 5 caracteres";
    usuario.setAttribute("style", "border-color: red");
    validUsuario = false;
  } else {
    labelUsuario.setAttribute("style", "color: green");
    labelUsuario.innerHTML = "Usuário";
    usuario.setAttribute("style", "border-color: green");
    validUsuario = true;
  }
});

senha.addEventListener("keyup", () => {
  if (senha.value.length <= 5) {
    labelSenha.setAttribute("style", "color: red");
    labelSenha.innerHTML = "Senha *Insira no minimo 6 caracteres";
    senha.setAttribute("style", "border-color: red");
    validSenha = false;
  } else {
    labelSenha.setAttribute("style", "color: green");
    labelSenha.innerHTML = "Senha";
    senha.setAttribute("style", "border-color: green");
    validSenha = true;
  }
});

confirmSenha.addEventListener("keyup", () => {
  if (senha.value != confirmSenha.value) {
    labelConfirmSenha.setAttribute("style", "color: red");
    labelConfirmSenha.innerHTML = "Confirmar Senha *As senhas não conferem";
    confirmSenha.setAttribute("style", "border-color: red");
    validConfirmSenha = false;
  } else {
    labelConfirmSenha.setAttribute("style", "color: green");
    labelConfirmSenha.innerHTML = "Confirmar Senha";
    confirmSenha.setAttribute("style", "border-color: green");
    validConfirmSenha = true;
  }
});

function cadastrar() {
  if (validNome && validUsuario && validSenha && validConfirmSenha) {
    let listaUser = JSON.parse(localStorage.getItem("listaUser") || "[]");

    listaUser.push({
      nomeCad: nome.value,
      userCad: usuario.value,
      senhaCad: senha.value
    });

    localStorage.setItem("listaUser", JSON.stringify(listaUser));

    msgSuccess.setAttribute("style", "display: block");
    msgSuccess.innerHTML = "<strong>Cadastrando usuário...</strong>";
    msgError.setAttribute("style", "display: none");
    msgError.innerHTML = "";

    setTimeout(() => {
      window.location.href =
        "https://cdpn.io/thicode/debug/ZELzYxV/dXAqBaRyvwJk";
    }, 3000);
  } else {
    msgError.setAttribute("style", "display: block");
    msgError.innerHTML =
      "<strong>Preencha todos os campos corretamente antes de cadastrar</strong>";
    msgSuccess.innerHTML = "";
    msgSuccess.setAttribute("style", "display: none");
  }
}

btn.addEventListener("click", () => {
  let inputSenha = document.querySelector("#senha");

  if (inputSenha.getAttribute("type") == "password") {
    inputSenha.setAttribute("type", "text");
  } else {
    inputSenha.setAttribute("type", "password");
  }
});

btnConfirm.addEventListener("click", () => {
  let inputConfirmSenha = document.querySelector("#confirmSenha");

  if (inputConfirmSenha.getAttribute("type") == "password") {
    inputConfirmSenha.setAttribute("type", "text");
  } else {
    inputConfirmSenha.setAttribute("type", "password");
  }
});

```
2ª parte em HTML

```
<head>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css">
  </head>
  
  <body>
  
    <div class='container'>
      <div class='card'>
        <h1> Cadastrar </h1>
  
        <div id='msgError'></div>
        <div id='msgSuccess'></div>
  
        <div class="label-float">
          <input type="text" id="nome" placeholder=" " required>
          <label id="labelNome" for="nome">Nome</label>
        </div>
  
        <div class="label-float">
          <input type="text" id="usuario" placeholder=" " required>
          <label id="labelUsuario" for="usuario">Usuário</label>
        </div>
  
        <div class="label-float">
          <input type="password" id="senha" placeholder=" " required>
          <label id="labelSenha" for="senha">Senha</label>
          <i id="verSenha" class="fa fa-eye" aria-hidden="true"></i>
  
        </div>
  
        <div class="label-float">
          <input type="password" id="confirmSenha" placeholder=" " required>
          <label id="labelConfirmSenha" for="confirmSenha">Confirmar Senha</label>
          <i id="verConfirmSenha" class="fa fa-eye" aria-hidden="true"></i>
        </div>
  
        <div class='justify-center'>
          <button onclick='cadastrar()'>Cadastrar</button>
        </div>
  
      </div>
    </div>
  </body>
  
  ```
  3ª parte em CSS
  
  ```
  @import url("https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap");

* {
  margin: 0;
  padding: 0;
  font-family: "Roboto", sans-serif;
}

body {
  background-image: url(https://i.imgur.com/XbRg9D7.png);
  background-repeat: no-repeat;
  background-size: cover;
  background-attachment: fixed;
}

.container {
  display: flex;
  justify-content: center;
  width: 100%;
  margin-top: 100px;
}

.card {
  background-color: #ffffff80;
  padding: 30px;
  border-radius: 4%;
  box-shadow: 3px 3px 1px 0px #00000060;
  width: 400px;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
  color: #0d009c;
}

.label-float input {
  width: 100%;
  padding: 5px 5px;
  display: inline-block;
  border: 0;
  border-bottom: 2px solid #0d009c;
  background-color: transparent;
  outline: none;
  min-width: 180px;
  font-size: 16px;
  transition: all 0.3s ease-out;
  border-radius: 0;
}

.label-float {
  position: relative;
  padding-top: 13px;
  margin-top: 5%;
  margin-bottom: 5%;
}

.label-float input:focus {
  border-bottom: 2px solid #4038a0;
}

.label-float label {
  color: #0d009c;
  pointer-event: none;
  position: absolute;
  top: 0;
  left: 0;
  margin-top: 13px;
  transition: all 0.3s ease-out;
}

.label-float input:focus + label,
.label-float input:valid + label {
  font-size: 13px;
  margin-top: 0;
  color: #4038a0;
}

button {
  background-color: transparent;
  border-color: #0d009c;
  color: #0d009c;
  padding: 7px;
  font-weight: bold;
  font-size: 12pt;
  margin-top: 20px;
  border-radius: 4px;
  cursor: pointer;
  outline: none;
  transition: all 0.4s ease-out;
}

button:hover {
  background-color: #0d009c;
  color: #fff;
}

.justify-center {
  display: flex;
  justify-content: center;
}

.fa-eye {
  position: absolute;
  top: 15px;
  right: 10px;
  cursor: pointer;
  color: #0d009c;
}

#msgError {
