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
    imagem: "https://img.ltwebstatic.com/images3_pi/2020/12/17/1608191555ab585116fb1b3f892150e679c960f03e_thumbnail_600x.webp"
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
    quantidade: 1,
    valorTotal: 49.9
  },
  {
    id: 2,
    nome: 'Calça',
    preco: 99.9,
    quantidade: 2,
    valorTotal: 199.8
  },
  {
    id: 3,
    nome: 'Meia',
    preco: 9.9,
    quantidade: 4,
    valorTotal: 39.6
  }
]


const enviar = ref(false)

function remover(index) {
  carrinho.value.splice(index, 1);
}

function diminuir(id) {
  if (produtos.value[id].quantidade > 0) {
    produtos.value[id].quantidade--;
  }
}

function adicionar(index) {
  if (produtos.value[index].quantidade > 0) {

    novoItem.value.id = produtos.value[index].id;
    novoItem.value.nome = produtos.value[index].nome;
    novoItem.value.preco = produtos.value[index].preco;
    novoItem.value.quantidade = produtos.value[index].quantidade;
    carrinho.value.push({ ...novoItem.value });
  } else {
    alert("Selecione a quantidade do produto desejado")
  }

}
</script>


<template>
<header class="nav">
      <h2>Loja Dev Web</h2>
      <button class="btnCarrinho" @click="enviar = true"> Carrinho</button>
    </header>


      <main class="container1" v-if="enviar==false">
    <div class="produtos-main">
      
      <div class="grid">

        <div class="produtos-item" v-for="(produto, index) in produtos" :key="index">
          
          <div class="colunas-produtos">
            <div>
              <img class="img" :src="produto.imagem" >
            </div>
            <div>
              <p class="info"> {{ produto.nome }}</p>
            </div>
            <div>
              <p class="info">R$:{{ produto.preco }}</p>
          </div>
          <div>
            <p class="info">Valor Total: R$:{{ produto.valorTotal }}</p>
          </div>
          
          <p v-for="(produto, key) in produtos" :key="key">{{ produto.key }}</p>
          
          
          <div class="bt">
            <button class="btProd" @click="produto.quantidade++">+</button>
            <p>{{ produto.quantidade }}</p>
            <button class="btProd" @click="diminuir(produto.id - 1)">-</button>
          </div>
          
          
        </div>
          
            <button class="botaoCarrinho" @click="adicionar(index)">Adicionar ao carrinho</button>
          
        </div>
      </div>

    </div>
    
  </main>
  <div v-else>
        <div class="carrinho">
          <h2 class="tituloCarrinho">Carrinho</h2>

          <div class="item" v-for="(item, index) in carrinho" :key="index"> 
            <p class="info">Nome: {{ item.nome }}</p>
            <p class="info">Preço: R$:{{ item.preco }}</p>
            <p class="info">Quantidade: {{ item.quantidade }}</p>
          </div>
          <div class="btFinal">
            <button class="btProd2" @click="remover(index)">Remover</button>
            <button @click="total" class="btProd2">Somar produtos</button>
          </div>
          <p class="info">valor Total:{{ valorTotal }}</p>
          <button type="submit" class="btFinalizar">finalizar compra</button>

        </div>
      </div>
</template>
<style scoped>

.grid{
  
  display: grid;
  grid-template-columns: 1fr 1fr;
}
.btnCarrinho {
  width: 220px;
  background-color: #1d0816;
  color: #fff;
  border: none;
  padding: 10px;
  border-radius: 5px;
  cursor: pointer;
  margin: 100px;
  margin-bottom: 55px;
  margin-top: 65px;
  transition: background-color 0.2s, color 0.2s;

}

.botaoCarrinho {
  width: 420px;
  background-color: #1d0816;
  color: #fff;
  border: none;
  padding: 10px;
  border-radius: 5px;
  cursor: pointer;
  margin: 40px;
  padding-left: 20px;
  margin-top: 20px;
  transition: background-color 0.2s, color 0.2s;
}

li {
  display: flex;
}

.bt {
  width: 50px;
  background-color: #ad4d4d00;
  display: inline-flex;
  align-items: center;
  justify-content: space-around;
  margin: 10px;
  padding-left: 220px;
}

.btFinal {
  margin-top: 20px;
  padding-left: 140px;
}

.btProd2 {
  background-color: #200919;
  border: none;
  border-radius: 5px;
  align-items: center;
  padding: 10px;
  border-radius: 5px;
  cursor: pointer;

  margin: 10px;

  color: #fff;

}

.nav{
  display: grid;
  grid-template-columns: 1fr 1fr;
}
.btProd {
  background-color: #200919;
  border: none;
  border-radius: 5px;
  align-items: center;
  padding: 10px;
  border-radius: 5px;
  cursor: pointer;
  margin: 10px;
  color: #fff;

}

.btCarrinho {
  border-radius: 20px;
}

h2 {
  margin: 20px;
  margin-left: 200px;
  text-align: center;
  font-size: 40px;
  font-family: 'Poppins', sans-serif;
  font-style: normal;
  margin-top: 60px;

}


.produtos-item {
  padding-top: 20px;
  
}

.produtos-main .produtos-item {

  background-color: rgba(231, 211, 228, 0.87);
  position: relative;
  width: 500px;
  margin: 50px 50px 50px 200px;
  border-radius: 8px;
  box-shadow: 0 4px 18px #2a2f430f;

}

.info {

  margin: 10px;
  text-align: center;
  font-size: 15px;
  font-family: 'Poppins', sans-serif;
  font-style: normal;
}

.carrinho {
  background-color: rgba(117, 6, 6, 0.315);
  position: relative;
  width: 500px;
  margin: 50px;
  border-radius: 8px;
  box-shadow: 0 4px 18px #2a2f430f;
}

.btFinalizar {
  width: 420px;
  background-color: #1d0816;
  color: #fff;
  border: none;
  padding: 10px;
  border-radius: 5px;
  cursor: pointer;
  margin: 40px;
  padding-left: 20px;
  margin-top: 20px;
  transition: background-color 0.2s, color 0.2s;
}
.img{
  width: 200px;
  margin-left: 150px;
}
</style>