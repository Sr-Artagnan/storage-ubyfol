<script>
    let page = 'Login'; 
    import PainelAdm from './PainelAdm.svelte'
    import Login from './Login.svelte';
    import Dashboard from'./Dashboard.svelte';
    console.log(page)
    
    function navigate(to) {
      page = to;
    }

    let showNotifications = false;

    function toggleNotifications() {
        showNotifications = !showNotifications;
    }

    let notifications = [
        "Itens em Itaguaí perto do vencimento",
        "Itens em Uberaba perto do vencimento",
        "Itens em Igarapava perto do vencimento",
        "Vendas de Potamol muito baixas em Maringá",
        "Vendas de Byofol em alta em Campo Florido",
        // ... outras notificações placeholder ...
    ];
</script>
  
<nav>
    <img src=".\Logo.png" alt="Logo">
    <button on:click={() => navigate('Login')}>Login</button>
    <button on:click={() => navigate('PainelAdm')}>Painel Administrador</button>
    <button on:click={() => navigate('Dashboard')}>Dashboard</button>
    <div class="notification-container">
        <button on:click={toggleNotifications}>
              🔔   <span class="badge">{notifications.length}</span>
        </button>
        {#if showNotifications}
        <div class="notification-dropdown">
            {#each notifications as notification}
                <div class="notification-item">
                    {notification}
                </div>
            {/each}
        </div>
        {/if}
    </div>
</nav>

<main>
    {#if page === 'Login'}
        <Login />
        {:else if page === 'PainelAdm'}
        <PainelAdm />
        {:else if page === 'Dashboard'}
        <Dashboard />
    {/if}
</main>


<style>
    /* Reset básico para remover margens e paddings padrões dos browsers */
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    nav {
        width: 200px; /* largura fixa para a barra de navegação */
        height: 100vh; /* altura total da tela */
        background-color: #333; /* cor de fundo da barra de navegação */
        position: fixed; /* fixa a barra de navegação */
        top: 0; /* no topo da tela */
        left: 0; /* e à esquerda da tela */
        display: flex;
        flex-direction: column; /* faz os botões serem empilhados verticalmente */
        align-items: center; /* centraliza os botões horizontalmente */
        padding-top: 2rem; /* um espaço no topo para começar a empilhar os botões */
    }

    img{
        width:80%;
    }

    button {
        margin-bottom: 1rem; /* espaço entre os botões */
        padding: 0.5rem 1rem; /* padding interno dos botões */
        font-size: 1rem;
        cursor: pointer;
        border: none;
        background-color: #EF2D38;
        color: #FFF;
        border-radius: 5px; /* bordas arredondadas */
        transition: background-color 0.3s; /* transição suave ao alterar a cor de fundo */
        position: relative;
    }

    button:hover {
        background-color: #d92632; /* cor de fundo ao passar o mouse */
    }

    main {
        margin-left: 220px; /* espaço à esquerda do conteúdo para não ficar sob a barra de navegação */
        padding: 2rem; /* um espaço interno para o conteúdo */
        width: calc(100% - 220px); /* a largura do conteúdo será a largura total da tela menos a largura da barra de navegação */
        overflow-y: auto; /* permite a rolagem vertical se o conteúdo for mais alto do que a tela */
    }
    .notification-container {
    position: relative;
    margin-top: 40vh;
}

.badge {
    background-color: #EE2D38;
    color: #FFF;
    border-radius: 50%;
    padding: 0.2rem 0.5rem;
    position: absolute;
    top: 0;
    right: 0;
    transform: translate(50%, -50%);
}

.notification-dropdown {
    background-color: #fff;
    position: absolute;
    left: 0;
    bottom: 100%;  /* alinha o dropdown acima do botão */
    border: 1px solid #ddd;
    border-radius: 8px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.4);
    max-height: 50vh; /* altura máxima para o dropdown */
    overflow-y: auto; /* adiciona barra de rolagem se necessário */
    width: 250px;
}

.notification-item {
    padding: 0.5rem 1rem;
    border-bottom: 1px solid #eee;
}

.notification-item:last-child {
    border-bottom: none;
}

</style>

