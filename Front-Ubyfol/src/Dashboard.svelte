<script>
    let products = [
        {
            id: 1,
            name: "Produto A",
            soldAmount: 150,
            stockKgOrL: 1000,
            price: 10,
        },
        {
            id: 2,
            name: "Produto B",
            soldAmount: 100,
            stockKgOrL: 500,
            price: 15,
        },
        {
            id: 3,
            name: "Produto C",
            soldAmount: 80,
            stockKgOrL: 750,
            price: 20,
        },
        {
            id: 4,
            name: "Produto D",
            soldAmount: 120,
            stockKgOrL: 400,
            price: 25,
        },
    ];

    let resellers = [
        { id: 1, name: "Revendedor A", sales: 350, region: "Triângulo Mineiro" },
        { id: 2, name: "Revendedor B", sales: 250, region: "Alto Parnaíba" },
        { id: 3, name: "Revendedor C", sales: 450, region: "Norte da Bahia" },
        { id: 4, name: "Revendedor D", sales: 320, region: "Grande Goiânia" },
    ];

    function mostSoldProducts() {
        return products.sort((a, b) => b.soldAmount - a.soldAmount);
    }

    function resellerInfo() {
        return resellers;
    }

    function stockKgOrLThisMonth() {
        return products.reduce(
            (total, product) => total + product.stockKgOrL,
            0
        );
    }

    function stockPercentageChange() {
        const previousMonthStockKgOrL = 2500; // Valor fictício
        const currentStock = stockKgOrLThisMonth();
        const change =
            ((currentStock - previousMonthStockKgOrL) /
                previousMonthStockKgOrL) *
            100;
        return change.toFixed(2);
    }

    function productsByRegion() {
        let regionCounts = {};

        resellers.forEach((reseller) => {
            if (!regionCounts[reseller.region]) {
                regionCounts[reseller.region] = 0;
            }
            regionCounts[reseller.region]++;
        });

        return Object.keys(regionCounts).map((region) => {
            return { region: region, count: regionCounts[region] };
        });
    }

</script>

<div class="dashboard">
    <div class="card">
        <h2>Produtos Mais Vendidos</h2>
        <ul>
            {#each mostSoldProducts() as product}
                <li>{product.name} - {product.soldAmount}</li>
            {/each}
        </ul>
    </div>
    

    <div class="card">
        <h2>Informações de Cada Revendedor</h2>
        <ul>
            {#each resellerInfo() as reseller}
                <li>{reseller.name} - {reseller.sales}</li>
            {/each}
        </ul>
    </div>

    <div class="card">
        <h2>Estoque Kg/L Neste Mês</h2>
        <p>{stockKgOrLThisMonth()} Kg/L</p>
    </div>

    <div class="card">
        <h2>Estoque R$ % Deste Mês Comparado com Mês Passado</h2>
        <p>{stockPercentageChange()}%</p>
    </div>

    <div class="card">
        <h2>Produtos Mais Vendidos</h2>
        <ul>
            {#each mostSoldProducts() as product}
                <li>{product.name} - Vendidos: {product.soldAmount} - Estoque: {product.stockKgOrL}Kg/L - Preço: ${product.price}</li>
            {/each}
        </ul>
    </div>
    
</div>

<style>
    body {
        font-family: Arial, sans-serif;
    }

    .dashboard {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: 20px;
        padding: 15px;
    }

    .card {
        padding: 10px;
        border: 1px solid #ccc;
        border-radius: 10px;
        background-color: #f9f9f9;
        box-shadow: 0px 5px 15px rgba(0, 0, 0, 0.3);
    }

    h2 {
        font-size: 18px;
        margin-bottom: 20px;
        color: #333;
        border-bottom: 2px solid #e0e0e0;
        padding-bottom: 10px;
    }

    ul {
        list-style-type: none;
        padding-left: 0;
    }

    li {
        padding: 10px 0;
        border-bottom: 1px dashed #ddd;
    }

    li:last-child {
        border-bottom: none;
    }

    .region-count {
        background-color: #e0e0e0;
        padding: 5px 10px;
        border-radius: 50px;
        font-weight: bold;
    }
</style>
