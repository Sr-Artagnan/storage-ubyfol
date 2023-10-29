<script>
    async function fazerLogin() {
        const usuario = document.getElementById('usuario').value;
        const senha = document.getElementById('senha').value;
        if (usuario === "admin" && senha === "12345") {
            alert("Login bem-sucedido!");
        } else {
            alert("Usuário ou senha inválidos!");
        }
    }
</script>


<style>
    .login-form {
        background-color: #fff;
        padding: 2vh 10vh;
        border-radius: 5%;
        box-shadow: 0 4px 20px rgba(0, 0, 0, 0.4);
        margin: auto;
        max-width: 500px;
    }

    h2 {
        color: #EE2D38;
        margin-bottom: 1.5rem;
    }

    .form-field {
        margin-bottom: 1.5rem;
    }

    label {
        display: block;
        margin-bottom: 0.5rem;
        color: #333;
        font-weight: bold;
    }

    input {
        width: 100%;
        padding: 0.75rem 1rem;
        border: 1px solid #ddd;
        border-radius: 8px;
        box-sizing: border-box;
        transition: border-color 0.3s, box-shadow 0.3s;
    }

    input:focus {
        border-color: #EE2D38;
        box-shadow: 0 0 5px rgba(238, 45, 56, 0.4);
        outline: none;
    }

    button {
        background-color: #EE2D38;
        color: #FFF;
        border: none;
        border-radius: 10%;
        padding: 0.75rem 1.5rem;
        cursor: pointer;
        transition: background-color 0.3s, transform 0.3s;
    }

    button:hover {
        background-color: #d92632;
        transform: translateY(-3px);
    }

    button:active {
        transform: translateY(0);
    }
</style>

<body>

<div class="login-form">
    <h2>Login</h2>
    <div class="form-field">
        <label for="usuario">Usuário:</label>
        <input type="text" id="usuario" placeholder="Digite seu usuário" />
    </div>
    <div class="form-field">
        <label for="senha">Senha:</label>
        <input type="password" id="senha" placeholder="Digite sua senha" />
    </div>
    <button on:click={fazerLogin}>Entrar</button>
</div>

</body>