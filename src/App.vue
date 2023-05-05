<script setup>
import { ref } from 'vue'
const produtos = ref([
    {
        id: 1,
        nome: 'Camiseta',
        preco: 49.90
    },
    {
        id: 2,
        nome: 'Calça',
        preco: 99.90
    },
    {
        id: 3,
        nome: 'Meia',
        preco: 9.90
    },
    {
        id: 4,
        nome: 'Sapato',
        preco: 199.90
    },
    {
        id: 5,
        nome: 'Boné',
        preco: 29.90
    },
    {
        id: 6,
        nome: 'Óculos',
        preco: 99.90
    },
    {
        id: 7,
        nome: 'Relógio',
        preco: 299.90
    },
    {
        id: 8,
        nome: 'Bermuda',
        preco: 79.90
    },
    {
        id: 9,
        nome: 'Cueca',
        preco: 19.90
    },
    {
        id: 10,
        nome: 'Meia',
        preco: 9.90
    }
])
const carrinho = [
    {
        id: 1,
        nome: 'Camiseta',
        preco: 49.90,
        quantidade: 1,
        valorTotal: 49.90
    },
    {
        id: 2,
        nome: 'Calça',
        preco: 99.90,
        quantidade: 2,
        valorTotal: 199.80
    },
    {
        id: 3,
        nome: 'Meia',
        preco: 9.90,
        quantidade: 4,
        valorTotal: 39.60
    }
]
function total() {
    for (let i = 0; i < carrinho.length; i++) {
        const element = valorTotal[i];
    }
}
function diminuir(){
    if(produtos.quantidade.value > 0){
        produtos.quantidade.value--
    }
}
function adicionar() {
    carrinho.value.push(produtos.value)
    carrinho.value = ''
}
function remover() {
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
            <button @click="remover">-</button>
            <button @click="diminuir">-</button>
        </li>
    </ul>

    <div class="container">
        <h2>Carrinho</h2>
        <button @click="total" class="botao">Somar produtos</button>
        <p>{{ valorTotal }}</p>
            <button type="submit" class="botao">finalizar compra</button>
    </div>
</template>