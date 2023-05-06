<script setup>
import { ref } from 'vue'

const produtos = ref([
    {
        id: 1,
        nome: 'Camiseta',
        preco: 49.90,
        quantidade: 0
    },
    {
        id: 2,
        nome: 'Calça',
        preco: 99.90,
        quantidade: 0
    },
    {
        id: 3,
        nome: 'Meia',
        preco: 9.90,
        quantidade: 0
    },
    {
        id: 4,
        nome: 'Sapato',
        preco: 199.90,
        quantidade: 0
    },
    {
        id: 5,
        nome: 'Boné',
        preco: 29.90,
        quantidade: 0
    },
    {
        id: 6,
        nome: 'Óculos',
        preco: 99.90,
        quantidade: 0
    },
    {
        id: 7,
        nome: 'Relógio',
        preco: 299.90,
        quantidade: 0
    },
    {
        id: 8,
        nome: 'Bermuda',
        preco: 79.90,
        quantidade: 0
    },
    {
        id: 9,
        nome: 'Cueca',
        preco: 19.90,
        quantidade: 0
    },
    {
        id: 10,
        nome: 'Meia',
        preco: 9.90,
        quantidade: 0
    }
])

const carrinho = [
    {
        id: 1,
        nome: 'Camiseta',
        preco: 49.90,
        quantidadeCarrinho: 1,
        valorTotal: 49.90
    },
    {
        id: 2,
        nome: 'Calça',
        preco: 99.90,
        quantidadeCarrinho: 2,
        valorTotal: 199.80
    },
    {
        id: 3,
        nome: 'Meia',
        preco: 9.90,
        quantidadeCarrinho: 4,
        valorTotal: 39.60
    }
]

function total() {
    for (let i = 0; i < carrinho.length; i++) {
        const valorTotal = valorTotal[i] + valorTotal;
    }
}

function diminuir(idProd) {
    if (produtos.value[idProd].quantidade > 0) {
        produtos.value[idProd].quantidade--
    }
}

function adicionarCarrinho() {
    carrinho.value.push(produtos.value);
    carrinho.value = ''
}

function removerCarrinho(key) {
    carrinho.value.splice(index, 1)
}

</script>
<template>

    
    <ul>
        <h2>Produtos</h2>
        <li v-for="(produto, index) in produtos" :key="index">
            <p>Nome: {{ produto.nome }}</p>
            <p>Preço: R$:{{ produto.preco }}</p>
            <p>Quantidade: {{ produto.quantidade }}</p>
            <p v-for="(produto, key) in produtos" :key="key">{{ produto.key }}</p>
            <button @click="produto.quantidade++">+</button>
            <button @click="diminuir(produto.id-1)">-</button>
        </li>
    </ul>

    <div class="container">
        <h2>Carrinho</h2>
        <div class="item" v-for="(item, index) in carrinho" :key="index">
            <p>Nome: {{ item.nome }}</p>
            <p>Preço: R$:{{ item.preco }}</p>
            <p>Quantidade: {{ item.quantidade }}</p>
        </div>
        <button @click="total" class="botao">Somar produtos</button>
        <p>{{ valorTotal }}</p>
            <button type="submit" class="botao">finalizar compra</button>
    </div>
</template>
<style scoped>
.botao {
    border: none;
    border-radius: 5px;
    font-weight: bold;
    font-size: 16px;
    padding: 7px 20px;
    background-color: #595C48;
    color: aliceblue;
    margin: 5px;
    width: 220px;
}
.container {
    font-size: 18px;
    background-color: #253B35;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    padding: 80px;
    border-radius: 15px;
    box-shadow: 0px 10px 40px #00000056;
    width: 400px;
    color: aliceblue;
  }

  li {
    list-style: none;
  }

.item {
    background-color: #253B35;
}
</style>