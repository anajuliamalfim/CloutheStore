<script setup>
import { ref, computed } from 'vue'
const frete = ref(0)

const conjuntos = ref([
  {
    id: 1,
    img: '/public/clothesIMG/alfaiatariaoffwhite.png',
    nome: 'Alfaiataria Off-White',
    tamanho: 'P', //autor
    preco: 120.90,
    quantidade: 1,
  },
  {
    id: 2,
    img: '/public/clothesIMG/azulclaroresort.png',
    nome: 'Azul Claro Resort',
    tamanho: 'M', //autor
    preco: 95.90,
    quantidade: 1,
  },
])

const texto = ref('')

const total = computed(() => {
  return conjuntos.value.reduce((total, conjunto) => total + conjunto.preco * conjunto.quantidade, 0)
})

const desconto = computed(() => {
  let subtotal = conjuntos.value.reduce((total, conjunto) => total + conjunto.preco * conjunto.quantidade, 0)
  return texto.value.toLowerCase() == 'lrv10' ? subtotal - subtotal * 0.1 : subtotal
})
</script>
<template>
  <main>
    <h1>Carrinho</h1>
    <section class="table">
      <table>
        <thead>
          <tr>
            <th>Nome</th>
            <th>Quantidade</th>
            <th>Subtotal</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(conjunto, id) in conjuntos" :key="id">
            <td>
              <div class="conjunto">
                <img :src="conjunto.img" alt="" />
                <div class="informacao">
                  <h3>{{ conjunto.nome }}</h3>
                  <p style="color: #4F4C57;">{{ conjunto.tamanho }}</p>
                  <p style="font-weight: 600">R$ {{ conjunto.preco }}</p>
                </div>
              </div>
            </td>
            <td>
              <div class="button">
                <button v-if="conjunto.quantidade > 1" @click="conjunto.quantidade--">-</button>
                <button v-else>-</button>
                <p>{{ conjunto.quantidade }}</p>
                <button @click="conjunto.quantidade++">+</button>
              </div>
            </td>
            <td>
              <p class="preco">R$ {{ (conjunto.preco * conjunto.quantidade).toFixed(2) }}</p>
            </td>
          </tr>
        </tbody>
      </table>
    </section>
    <router-link to="/" exact><button class="voltar">Voltar pra loja</button></router-link>
    <section style="display: flex">
      <div class="cupom">
        <input type="text" v-model="texto" placeholder="Código do cupom" />
        <button type="submit">Inserir Cupom</button>
      </div>
      <div id="total" style="border: 1px solid black">
        <h3>Total da Compra</h3>
        <ul>
          <li>
            <p class="parametro">Produtos:</p>
            <p>R$ {{ total.toFixed(2).replace('.', ',') }}</p>
          </li>
          <li>
            <p class="parametro">Frete:</p>
            <p v-if="frete == 0">GRÁTIS</p>
            <p v-else>Frete: {{ frete }}</p>
          </li>
          <li>
            <p class="parametro">Total:</p>
            <p>R$ {{ desconto.toFixed(2).replace('.', ',') }}</p>
          </li>
        </ul>
      <button>Ir
            para o pagamento</button>
      </div>
    </section>
  </main>
</template>
<style scoped>
main {
  margin: 10vw 5vw 10vw 5vw;
}

h1 {
  color: #27ae60;
  font-size: 2.5rem;
  font-weight: 500;
  margin-bottom: 2vw;
}

table {
  border-collapse: collapse;
  margin: 0 auto;
  width: 90vw;
  height: 30vw;
}

thead {
  th {
    font-size: 1.2rem;
    padding-bottom: 1.5vw;
    font-weight: bold;
    border-bottom: 1px solid #27ae60;
  }
}

tbody {
  tr td {
    border-bottom: 1px solid #c4c4c4;
  }

  img {
    margin: 1vw;
    height: 15vw;
    width: auto;
  }

  .livro {
    display: flex;
    padding: 1vw 0 1vw 0;

    div {
      padding: 1vw 14vw 0 0;
    }

    div h3 {
      font-size: 1.5rem;
      margin-bottom: 1vw;
      font-weight: 500;
      font-family: 0.3rem;
    }

    p {
      margin-bottom: 1vw;
    }
  }

  .button {
    display: flex;
    border: 1px solid black;
    justify-content: center;
    align-items: center;
    padding: 1vw;
    transform: translateY(-7vw);

    button {
      background-color: white;
      border: none;
      padding: 0 1.5vw 0 1.5vw;
      cursor: pointer;
    }
  }

  .preco {
    padding-left: 17vw;
    padding-right: 5vw;
    font-weight: 700;
    font-size: 1.1rem;
    transform: translate(-3.5vw, -7vw);
  }
}

.voltar {
  margin: 2vw 0 0 0.5vw;
  height: 3vw;
  width: 14vw;
  background-color: white;
  border: 1px solid #c4c4c4;
  border-radius: 4px;
  font-size: 1.1rem;
}

.voltar:hover {
  background-color: #27ae60;
  color: white;
}

.cupom {
  margin-top: 6vw;

  input {
    height: 3vw;
    width: 20vw;
    margin-right: 1vw;
    align-items: center;
    font-size: 1.2rem;
  }

  input::placeholder {
    margin-left: 5vw;
    font-size: 1.2rem;
  }

  button {
    color: white;
    background-color: #27ae60;
    height: 3vw;
    width: 13vw;
    border: none;
    border-radius: 4px;
    font-size: 1.1rem;
    cursor: pointer;
  }

  button:hover {
    background-color: #219752;
  }
}

#total {
  margin: 5vw 0 0 12vw;
  padding: 2vw;

  h3 {
    font-size: 1.1rem;
    font-weight: 700;
    padding: 0 0 1vw 0;
    text-align: left;
  }

  ul {
    list-style: none;
  }

  li {
    display: flex;
    justify-content: space-between;
    padding: 1vw 0 1vw 0;
    border-bottom: 1px solid #c4c4c4;
  }

  .parametro {
    margin-right: 10vw;
    padding-right: 7vw;
  }

  button {
    color: white;
    background-color: #27ae60;
    height: 3vw;
    width: 15vw;
    border: none;
    border-radius: 4px;
    display: block;
    margin: 2vw auto 0 auto;
    font-size: 1.1rem;
    cursor: pointer;
  }

  button:hover {
    background-color: #219752;
  }
}
</style>
