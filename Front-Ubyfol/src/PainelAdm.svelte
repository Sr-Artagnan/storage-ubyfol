<script>
    let products = [
        {
            Produto: "Byofol",
            Volume: "50",
            Soma: "R$ 220,00",
            Municipio: "Uberlândia",
            Estoque: "100",
            Data:"28/10/23",
            Gerente: "Adriano Teixeira",
            Observacao: "",
        },
        {
            Produto: "Potamol",
            Volume: "75",
            Soma: "R$ 2000,00",
            Municipio: "Igarapava/SP",
            Estoque: "150",
            Data:"28/10/23",
            Gerente: "Adriano Teixeira",
            Observacao: "",
        },
        {
            Produto: "Reduphol Max",
            Volume: "45",
            Soma: "R$ 350,00",
            Municipio: "Campo Florido/MG",
            Estoque: "60",
            Data:"28/10/23",
            Gerente: "Adriano Teixeira",
            Observacao: "",
        },
        {
            Produto: "Verdatto",
            Volume: "90",
            Soma: "R$ 225,00",
            Municipio: "Araras/SP",
            Estoque: "80",
            Data:"27/10/23",
            Gerente: "Adriano Teixeira",
            Observacao: "",
        },
        {
            Produto: "Byofol",
            Volume: "30",
            Soma: "R$ 1900,00",
            Municipio: "Patrocínio/MG",
            Estoque: "120",
            Data:"27/10/23",
            Gerente: "Adriano Teixeira",
            Observacao: "",
        },
        {
            Produto: "Reduphol Max",
            Volume: "45",
            Soma: "R$ 350,00",
            Municipio: "Uberaba/MG",
            Estoque: "60",
            Data:"24/10/23",
            Gerente: "Adriano Teixeira",
            Observacao: "",
        },
        {
            Produto: "Verdatto",
            Volume: "90",
            Soma: "R$ 225,00",
            Municipio: "Miguelópolis/SP",
            Estoque: "80",
            Data:"24/10/23",
            Gerente: "Adriano Teixeira",
            Observacao: "",
        },
    ];

    let filter = {
        Produto: "",
        Volume: "",
        Soma: "",
        Municipio: "",
        Estoque: "",
        Data:"",
        Gerente: "",
        Observacao: "",
    };

    const filteredProducts = () => {
        return products.filter((product) => {
            for (const key in filter) {
                if (
                    filter[key] &&
                    product[key]
                        .toString()
                        .toLowerCase()
                        .indexOf(filter[key].toLowerCase()) === -1
                ) {
                    return false;
                }
            }
            return true;
        });
    };

    const fetchProducts = async () => {
        // Substitua pela URL da sua API.
        const response = await fetch("https://api.example.com/products");
        products = await response.json();
    };
    //fetchProducts();

    const generateReport = () => {
        // Implemente a lógica para gerar um relatório em documento.
        alert("Função de gerar relatório ainda não implementada.");
    };

    let displayedProducts = [];

    $: displayedProducts = products.filter((product) => {
        for (const key in filter) {
            if (
                filter[key] &&
                product[key]
                    .toString()
                    .toLowerCase()
                    .indexOf(filter[key].toLowerCase()) === -1
            ) {
                return false;
            }
        }
        return true;
    });
</script>

<header>
    <h1>Painel de Administração - Gestão de Produtos</h1>
</header>


<table>
    <thead>
        <tr>
            <th>
                <select bind:value={filter.Produto}>
                    <option value="">Todos</option>
                    {#each [...new Set(products.map((product) => product.Produto))] as item}
                        <option value={item}>{item}</option>
                    {/each}
                </select>
            </th>

            <th>
                <select bind:value={filter.Volume}>
                    <option value="">Todos</option>
                    {#each [...new Set(products.map((product) => product.Volume))] as item}
                        <option value={item}>{item}</option>
                    {/each}
                </select>
            </th>

            <th>
                <select bind:value={filter.Soma}>
                    <option value="">Todos</option>
                    {#each [...new Set(products.map((product) => product.Soma))] as item}
                        <option value={item}>{item}</option>
                    {/each}
                </select>
            </th>

            <th>
                <select bind:value={filter.Municipio}>
                    <option value="">Todos</option>
                    {#each [...new Set(products.map((product) => product.Municipio))] as item}
                        <option value={item}>{item}</option>
                    {/each}
                </select>
            </th>

            <th>
                <select bind:value={filter.Estoque}>
                    <option value="">Todos</option>
                    {#each [...new Set(products.map((product) => product.Estoque))] as item}
                        <option value={item}>{item}</option>
                    {/each}
                </select>
            </th>

            <th>
                <select bind:value={filter.Data}>
                    <option value="">Todos</option>
                    {#each [...new Set(products.map((product) => product.Data))] as item}
                        <option value={item}>{item}</option>
                    {/each}
                </select>
            </th>

            <th>
                <select bind:value={filter.Gerente}>
                    <option value="">Todos</option>
                    {#each [...new Set(products.map((product) => product.Gerente))] as item}
                        <option value={item}>{item}</option>
                    {/each}
                </select>
            </th>

            <th>Observação</th>
        </tr>

        <tr>
            <th>Produto</th>
            <th>Volume Escoado</th>
            <th>Valores R$ Estoque</th>
            <th>Município/UF</th>
            <th>Estoque Atual</th>
            <th>Data</th>
            <th>Gerente</th>
            <th>Observação</th>
        </tr>
    </thead>

    <tbody>
        {#each displayedProducts as product}
            <tr>
                <td>{product.Produto}</td>
                <td>{product.Volume}</td> 
                <td>{product.Soma}</td>
                <td>{product.Municipio}</td>
                <td>{product.Estoque}</td>
                <td>{product.Data}</td>
                <td>{product.Gerente}</td>
                <td>{product.Observacao}</td>
            </tr>
        {/each}
    </tbody>
    
</table>


<style>
    /* Reset básico */
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        font-family: Arial, sans-serif;
    }

    header {
        background-color: #EE2D38;
        color: whitesmoke;
        padding: 2vh 0;
        text-align: center;
        box-shadow: 0 3px 15px rgba(0, 0, 0, 0.4);
    }

    table {
        border-collapse: collapse;
        background-color: #fff;
        box-shadow: 0 3px 15px rgba(0, 0, 0, 0.4);
    }

    th,
    td {
        border: 1px solid #333;
        padding: 1rem;
    }

    th {
        background-color: #333;
        color: whitesmoke;
    }

    td {
        text-align: center;
    }

    tr:hover {
        background-color: #f5f5f5;
    }
    select {
        padding: 0.5rem;
        border: 1px solid #bbb;
        font-size: 1rem;
        border-radius: 5px;
        width: 100%;
        box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.1);
        background-color: #f5f5f5;
    }
</style>
