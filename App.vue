<script setup>
import { ref } from 'vue'

const novoItem = ref({
    id: 0,
    nome: '',
    preco: 0,
    quantidade: 1,
})

const produtos = ref([
  {
    id: 1,
    nome: 'Camiseta',
    preco: 49.9,
    quantidade: 0,
    imagem: "imagens/camiseta.png"
  },
  {
    id: 2,
    nome: 'Calça',
    preco: 99.9,
    quantidade: 0,
    imagem: "imagens/camiseta.png"
  },
  {
    id: 3,
    nome: 'Meia',
    preco: 9.9,
    quantidade: 0,
    imagem: "imagens/camiseta.png"
  },
  {
    id: 4,
    nome: 'Sapato',
    preco: 199.9,
    quantidade: 0,
    imagem: "imagens/camiseta.png"
  },
  {
    id: 5,
    nome: 'Boné',
    preco: 29.9,
    quantidade: 0,
    imagem: "imagens/camiseta.png"
  },
  {
    id: 6,
    nome: 'Óculos',
    preco: 99.9,
    quantidade: 0,
    imagem: "imagens/camiseta.png"
  },
  {
    id: 7,
    nome: 'Relógio',
    preco: 299.9,
    quantidade: 0,
    imagem: "imagens/camiseta.png"
  },
  {
    id: 8,
    nome: 'Bermuda',
    preco: 79.9,
    quantidade: 0,
    imagem: "imagens/camiseta.png"
  },
  {
    id: 9,
    nome: 'Cueca',
    preco: 19.9,
    quantidade: 0,
    imagem: "imagens/camiseta.png"
  },
  {
    id: 10,
    nome: 'Meia',
    preco: 9.9,
    quantidade: 0,
    imagem: "imagens/camiseta.png"
  },
])

const carrinho = [
  {
    id: 1,
    nome: 'Camiseta',
    preco: 49.9,
    quantidadeCarrinho: 1,
    valorTotal: 49.9
  },
  {
    id: 2,
    nome: 'Calça',
    preco: 99.9,
    quantidadeCarrinho: 2,
    valorTotal: 199.8
  },
  {
    id: 3,
    nome: 'Meia',
    preco: 9.9,
    quantidadeCarrinho: 4,
    valorTotal: 39.6
  }
]
const enviar = ref(false)

function total() {
  for (let i = 0; i < carrinho.length; i++) {
    const valorTotal = valorTotal[i] + valorTotal
  }
}

function diminuir(idProd) {
  if (produtos.value[idProd].quantidade > 0) {
    produtos.value[idProd].quantidade--;
  }
}

function adicionarCarrinho(index) {
  if (produtos.value[index].quantidade > 0) {
    novoItem.value.id = produtos.value[index].id;
    novoItem.value.nome = produtos.value[index].nome;
    novoItem.value.preco = produtos.value[index].preco;
    novoItem.value.quantidade = produtos.value[index].quantidade;
    carrinho.value.push({ ...novoItem.value });
  }
  else {
    alert("Selecione a quantidade do produto desejado")
  }

}

function removerCarrinho(index) {
  carrinho.value.splice(index, 1)
}
</script>
<template>




  <ul class="produtos-main">
    <h2>Loja Dev Web</h2>

    <li class="produtos-item" v-for="(produto, index) in produtos" :key="index">
      <div>
        <p>Imagem: {{ produto.imagem }}</p>
      </div>
      <div>
        <p>Nome: {{ produto.nome }}</p>
      </div>
      <div>
        <p>Preço: R$:{{ produto.preco }}</p>
      </div>
      <div>
        <p>Valor Total: R$:{{ produto.valorTotal }}</p>
      </div>
      <p v-for="(produto, key) in produtos" :key="key">{{ produto.key }}</p>
      <div class="bt">
        <button class="btProd" @click="produto.quantidade++">+</button>
        <p>{{ produto.quantidade }}</p>
        <button class="btProd" @click="diminuir">-</button>
      </div>
      <div>
        <button class="btCarrinho" @click="adicionarCarrinho(index)">Adicionar ao carrinho</button>
      </div>
    </li>
  </ul>
  <button class="btprod" @click="enviar=true"> Carrinho</button>
<div v-if="enviar">
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
</div>
</template>
<style scoped>
.botao {
  border: none;
  border-radius: 5px;
  font-weight: bold;
  font-size: 16px;
  padding: 7px 20px;
  background-color: #be92e7;
  color: aliceblue;
  margin: 5px;
  width: 220px;
}

.container {
  font-size: 18px;
  background-color: #b376aa;
  padding: 80px;
  border-radius: 15px;
  box-shadow: 0px 10px 40px #00000056;
  width: 400px;
  color: black;
}

li {
  list-style: none;
  justify-content: space-around;
  display: flex;
}



.bt {
  background-color: #ccc;
  display: inline-flex;
  align-items: center;
  padding: 5px 0;
  justify-content: space-around;
  min-width: 60px;
  border-radius: 20px;
}

.btProd {
  background: transparent;
  border: 0;
  align-items: center;
  padding: 0 10px;
}

.btCarrinho {
  margin: 10px;
  background-color: #9484cf;
  display: inline-flex;
  align-items: center;
  padding: 5px 0;
 
  min-width: 60px;
  border-radius: 20px;
}

h2 {
  padding: 50px 0;
  text-align: center;
  font-size: 40px;
}

.produtos-main .produtos-item {
  background-color: white;
  position: relative;
  width: 100%;
  margin: 30px 0;
  border-radius: 8px;
  box-shadow: 0 4px 18px #2a2f430f;
  justify-content: space-around;
}</style>