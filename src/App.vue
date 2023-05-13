<script setup>
import { ref } from 'vue'

const produtos = ref([
  {
    id: 1,
    nome: 'Camiseta',
    preco: 49.9,
    quantidade: 1,
    imagem: "https://img.ltwebstatic.com/images3_pi/2020/12/17/1608191555ab585116fb1b3f892150e679c960f03e_thumbnail_600x.webp"
  },
  {
    id: 2,
    nome: 'Calça',
    preco: 99.9,
    quantidade: 1,
    imagem: "https://img.ltwebstatic.com/images3_pi/2022/06/02/165415761378fbdf3fd7fac568b458edd28b11815c_thumbnail_220x293.webp"
  },
  {
    id: 3,
    nome: 'Meia',
    preco: 9.9,
    quantidade: 1,
    imagem: "https://img.ltwebstatic.com/images3_pi/2022/03/22/16479445086297ada5b4c151b07fb387f30a9f0e67_thumbnail_600x.webp"
  },
  {
    id: 4,
    nome: 'Sapato',
    preco: 199.9,
    quantidade: 1,
    imagem: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRoClmr4WfyVpH5xG-SOxdWcLZlizi12Z09NnHpcVLr4eIQkKzX9UOV226izNISSZ3u8S8&usqp=CAU"
  },
  {
    id: 5,
    nome: 'Boné',
    preco: 29.9,
    quantidade: 1,
    imagem: "data:image/jpeg;base64,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"
  },
  {
    id: 6,
    nome: 'Óculos',
    preco: 99.9,
    quantidade: 1,
    imagem: "data:image/jpeg;base64,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"
  },
  {
    id: 7,
    nome: 'Relógio',
    preco: 299.9,
    quantidade: 1,
    imagem: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRu5SMnq_IychNGX9Q9pZhQAixDy2XNuV_7Pg&usqp=CAU"
  },
  {
    id: 8,
    nome: 'Saia',
    preco: 79.9,
    quantidade: 1,
    imagem: "data:image/jpeg;base64,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"
  }
])
const avf = (value) => 'R$ ' + value.toFixed(2).replace('.', ',')
let enviar = ref(false)
let carrinho = ref([])
let valorcarrinho = ref(0)

function adicionarCarrinho(item) {
  const index = carrinho.value.findIndex((x) => x.codigo === item.id)
  if (index > -1) {
    alert('Item já está no carrinho!')
  } else {
    carrinho.value.push({
      codigo: item.id,
      nome: item.nome,
      preco: item.preco,
      quantidade: item.quantidade,
      valortotal: item.preco * item.quantidade
    })
    calculaCarrinho()
  }
}

function calculaCarrinho() {
  valorcarrinho.value = 0
  for (let index = 0; index < carrinho.value.length; index++) {
    valorcarrinho.value = valorcarrinho.value + carrinho.value[index].valortotal
  }
}

function adicionarQuantidade(index) {
  produtos.value[index].quantidade++
}

function removerQuantidade(index) {
  if (produtos.value[index].quantidade > 1) {
    produtos.value[index].quantidade--
  }
}

function limpaCarrinho() {
  carrinho.value = []
  valorcarrinho.value = 0
}
function remover(index) {
  carrinho.value.splice(index, 1)
  calculaCarrinho()
}
function verCarrinho() {
  if (carrinho.value < [0]) {
    alert('Carrinho está vazio!')
  } else {
    enviar.value = !enviar.value
  }
}

</script>

<template>
  <header class="nav">
  <h2>Loja Dev Web</h2>
  <button class="btnCarrinho" 
      aria-haspopup="true" aria-expanded="false" @click="verCarrinho">Carrinho</button>
    </header>

    

  <div class="carrinho">
    
    <div class="" v-if="enviar">
      <div class="">
        <div v-for="(item, index) in carrinho" :key="index" class="item-carrinho">
        <div class="carrinhoItens">
          <p class="infoCarrinho">Produto: {{ item.nome }}</p>
          <p class="infoCarrinho">Preço:{{ avf(item.preco) }}</p>
          <p class="infoCarrinho">Quantidade: {{ item.quantidade }}</p>
        </div>
        </div>
      </div>
      <div class="carrinho">
        <div class="carrinhoItens">
        <p class="infoCarrinho">Valor total: {{ avf(valorcarrinho) }}</p>
      </div>
        <div class="botoesCarrinho">
        <button class="btnCarrinho" @click="remover(index)">remover</button>
        <button class="btnCarrinho" @click="limpaCarrinho()">limpar carrinho</button>
        <button class="btnCarrinho" @click="enviar = !enviar">Fechar Carrinho</button>
      </div>
      </div>
    </div>
  </div>


 <div class="produtos-main">
      
      <div class="container">
    
      <div class="produtos-item" v-for="(item, index) in produtos" :key="index">
        <div class="colunas-produtos">
          <div>
              <img class="img" :src="item.imagem" >
            </div>
        <div>
        <p class="info">  {{ item.nome }}</p>
      </div>
    <div>
        <p class="info"> {{ avf(item.preco) }}</p>
      </div>
    <div>
        <p class="info">Quantidade: {{ item.quantidade }}</p>
      </div>
        <div class="bts">
          <button class="bt" @click="adicionarCarrinho(item)">adicionar ao carrinho</button>
          <button class="bt" @click="adicionarQuantidade(item.id - 1)">+</button>
          <button class="bt" @click="removerQuantidade(index)">-</button>
        </div>
      </div>
      </div>
  </div>
</div>
</template>

<style scoped>

h2 {
  margin: 20px;
  margin-left: 200px;
  text-align: center;
  font-size: 40px;
  font-family: 'Poppins', sans-serif;
  font-style: normal;
  margin-top: 60px;

}
.nav{
  display: grid;
  grid-template-columns: 1fr 1fr;
  margin-left: 330px;
  margin-top: 30px;
}
.btnCarrinho {
  width: 220px;
  background-color: #1d0816;
  color: #fff;
  border: none;
  padding: 10px;
  border-radius: 5px;
  cursor: pointer;
  margin: 50px;
  margin-bottom: 55px;
  margin-top: 65px;
  transition: background-color 0.2s, color 0.2s;

}
.info {

  margin: 10px;
  text-align: center;
  font-size: 15px;
  font-family: 'Poppins', sans-serif;
  font-style: normal;
  color:rgb(218, 218, 218);
}

.bt{
  background-color: rgb(218, 218, 218);
  border: none;
  border-radius: 5px;
  align-items: center;
  padding: 10px;
  border-radius: 5px;
  cursor: pointer;
  margin: 10px;
  color: #1f1b1b;
 
}
.container{
  
  display: grid;
  grid-template-columns: 1fr 1fr;
}

.produtos-item {
  padding-top: 20px;
  
}

.produtos-main .produtos-item {

  background-color: rgb(107, 101, 106);
  position: relative;
  width: 500px;
  margin: 50px 50px 50px 200px;
  border-radius: 8px;
  box-shadow: 0 4px 18px #05070c0f;

}
.bts{
  margin: 10px;
  padding-left: 100px;
 
}
.img{
  width: 200px;
  margin-left: 150px;
  border-radius: 10px;
}
.infoCarrinho {

margin: 10px;
text-align: center;
font-size: 15px;
font-family: 'Poppins', sans-serif;
font-style: normal;
color:rgb(8, 6, 6);
}
.botoesCarrinho{
  padding-left: 340px;
}
.carrinhoItens{
  padding-left: 300px;
}




</style>