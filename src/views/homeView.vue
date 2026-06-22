<script setup>
import { computed } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const produtosFiltrados = computed(() => {
  const termo = (route.query.q || '').toLowerCase()

  if (!termo) return produtos

  return produtos.filter(produto =>
    produto.nome.toLowerCase().includes(termo)
  )
})
const produtos = [
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
  {
    id: 3,
    img: '/public/clothesIMG/azulserenity.png',
    nome: 'Azul Serenity',
    tamanho: 'P',
    preco: 110.90,
  },
  {
   id: 4,
    img: '/public/clothesIMG/begealfaiatado.png',
    nome: 'Alfaiataria Bege',
    tamanho: 'M',
    preco: 120.90,
  },
  {
   id: 5,
    img: '/public/clothesIMG/brancoboho.png',
    nome: 'Branco Boho',
    tamanho: 'P',
    preco: 130.90,
  },
  {
    id: 6,
    img: '/public/clothesIMG/brancoecinto.png',
    nome: 'Branco Afivelado',
    tamanho: 'G',
    preco: 110.90,
  },
  {
    id: 7,
    img: '/public/clothesIMG/eleganciacreme.png',
    nome: 'Elegante Cremeado',
    tamanho: 'P',
    preco: 90.90,
  },
  {
    id: 8,
    img: '/public/clothesIMG/linhonatural.png',
    nome: 'Linho Natural',
    tamanho: 'P',
    preco: 130.90,
  },
]
//autorMes = colecaoMes
</script>

<template>
  <main>
       <section class="banner">
  <div class="fundo">
    <img class="logo" src="/public/otherIMG/logo.png" alt="logo">

    <h1><span>VERÃO</span> QUE INSPIRA</h1>
    <p>Peças leves, cores vibrantes e muito estilo para todos os momentos.</p>
  </div>
      <div class="text">
        <div class="colecaoMes">
          <img src="/public/otherIMG/fundo.png" alt="">
<div class="fundodois">
<h1>VERÃO</h1>
<p>Conjuntos</p>
<p>50%</p>
<p>OFF</p>
</div>
        </div>
      </div>
    </section>
    <section class="barraCentral">
      <ul>
        <li>
          <span><img src="../../public/otherIMG/caminhao.png" alt="caminhao"></span>
          <p>Frete grátis para SC</p>
        </li>
        <li class="meio">
          <span><img src="../../public/otherIMG/estrela.png" alt="estrela"></span>
          <p>Livros recomendados</p>
        </li>
        <li>
          <span><img src="../../public/otherIMG/cabide.png" alt="cabide"></span>
          <p>Mais vendidos</p>
        </li>
      </ul>

    </section>
    <section class="conjuntoss">
      <div>
        <h2>Lançamentos</h2>
      </div>
      <div class="tabela">
<div v-for="conjunto in produtosFiltrados" :key="conjunto.id" class="conjunto">
            <img :src="conjunto.img" alt="">
          <p class="nome">{{ conjunto.nome }}</p>
          <p class="tamanho">{{ conjunto.tamanho }}</p>
          <p class="preco">R$ {{ conjunto.preco }} <img src="../../public/otherIMG/coracao.png" alt="Coração"></p>
          <button class="botaoComprar">
            <img src="../../public/otherIMG/carrinho.png" alt="comprar">
            <p>Comprar</p>
          </button>
        </div>
      </div>
    </section>
  </main>
</template>
<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

main {
  font-family: 'Segoe UI', sans-serif;
  background-color: #faf8f5;
  color: #2c2c2c;
}

.banner {
  display: flex;
  align-items: stretch;
  min-height: 90vh;
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
  overflow: hidden;
}

.fundo {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 60px 64px;
  gap: 20px;
}

.logo {
  width: 400px;
  margin-bottom: 12px;
}

.fundo h1 {
  font-size: clamp(2.4rem, 5vw, 4rem);
  font-weight: 800;
  color: #ffffff;
  line-height: 1.1;
  letter-spacing: -1px;
  text-transform: uppercase;
}

.fundo h1 span {
  color: #e8c97e;
}

.fundo > p {
  font-size: 1.1rem;
  color: #c9d1d9;
  max-width: 360px;
  line-height: 1.7;
}

.text {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 40px;
}

.colecaoMes {
  position: relative;
  width: 100%;
  max-width: 420px;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 30px 80px rgba(0, 0, 0, 0.5);
}

.colecaoMes img {
  width: 100%;
  height: 480px;
  object-fit: cover;
  display: block;
}

.fundodois {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  padding: 28px 28px 24px;
  background: linear-gradient(to top, rgba(0,0,0,0.85) 0%, transparent 100%);
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.fundodois h1 {
  font-size: 1rem;
  font-weight: 600;
  letter-spacing: 4px;
  color: #e8c97e;
  text-transform: uppercase;
}

.fundodois p:nth-child(2) {
  font-size: 1.4rem;
  font-weight: 700;
  color: #ffffff;
}

.fundodois p:nth-child(3) {
  font-size: 3rem;
  font-weight: 900;
  color: #ffffff;
  line-height: 1;
}

.fundodois p:nth-child(4) {
  font-size: 1.4rem;
  font-weight: 700;
  color: #e8c97e;
  letter-spacing: 2px;
}

/* ===== BARRA CENTRAL ===== */
.barraCentral {
  background-color: #1a1a2e;
  padding: 20px 64px;
}

.barraCentral ul {
  display: flex;
  list-style: none;
  justify-content: center;
  align-items: center;
  gap: 0;
}

.barraCentral li {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 16px 48px;
  flex: 1;
  justify-content: center;
}

.barraCentral li.meio {
  border-left: 1px solid rgba(255,255,255,0.15);
  border-right: 1px solid rgba(255,255,255,0.15);
}

.barraCentral li span {
  width: 36px;
  height: 36px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.barraCentral li span img {
  width: 28px;
  height: 28px;
  object-fit: contain;
  filter: brightness(0) invert(1);
  opacity: 0.85;
}

.barraCentral li p {
  font-size: 0.9rem;
  font-weight: 500;
  color: #c9d1d9;
  letter-spacing: 0.3px;
}

.conjuntoss {
  padding: 72px 64px;
}

.conjuntoss > div:first-child {
  margin-bottom: 48px;
}

.conjuntoss h2 {
  font-size: 2rem;
  font-weight: 800;
  color: #1a1a2e;
  letter-spacing: -0.5px;
  position: relative;
  display: inline-block;
}

.conjuntoss h2::after {
  content: '';
  position: absolute;
  bottom: -8px;
  left: 0;
  width: 48px;
  height: 3px;
  background-color: #e8c97e;
  border-radius: 2px;
}

.tabela {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 28px;
}

.conjunto {
  background-color: #ffffff;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 2px 12px rgba(0,0,0,0.07);
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  display: flex;
  flex-direction: column;
}

.conjunto:hover {
  transform: translateY(-6px);
  box-shadow: 0 12px 32px rgba(0,0,0,0.13);
}

.conjunto > img {
  width: 100%;
  height: 260px;
  object-fit: cover;
  display: block;
}

.conjunto .nome {
  font-size: 0.95rem;
  font-weight: 700;
  color: #1a1a2e;
  padding: 16px 16px 4px;
}

.conjunto .tamanho {
  font-size: 0.78rem;
  color: #888;
  padding: 0 16px 4px;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.conjunto .preco {
  font-size: 1rem;
  font-weight: 700;
  color: #1a1a2e;
  padding: 0 16px 12px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: auto;
}

.conjunto .preco img {
  width: 18px;
  height: 18px;
  opacity: 0.5;
  cursor: pointer;
  transition: opacity 0.2s, transform 0.2s;
}

.conjunto .preco img:hover {
  opacity: 1;
  transform: scale(1.2);
}

/* ===== BOTÃO COMPRAR ===== */
.botaoComprar {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  width: calc(100% - 32px);
  margin: 0 16px 16px;
  padding: 12px;
  background-color: #1a1a2e;
  color: #ffffff;
  border: none;
  border-radius: 10px;
  font-size: 0.9rem;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.2s ease, transform 0.15s ease;
  letter-spacing: 0.3px;
}

.botaoComprar:hover {
  background-color: #e8c97e;
  color: #1a1a2e;
  transform: scale(1.02);
}

.botaoComprar img {
  width: 18px;
  height: 18px;
  object-fit: contain;
  filter: brightness(0) invert(1);
  transition: filter 0.2s;
}

.botaoComprar:hover img {
  filter: brightness(0);
}

.botaoComprar p {
  margin: 0;
}

/* ===== RESPONSIVO ===== */
@media (max-width: 768px) {
  .banner {
    flex-direction: column;
    min-height: auto;
  }

  .fundo {
    padding: 48px 28px 32px;
  }

  .text {
    padding: 0 28px 48px;
  }

  .barraCentral {
    padding: 12px 20px;
  }

  .barraCentral li {
    padding: 12px 16px;
    gap: 8px;
  }

  .barraCentral li p {
    font-size: 0.75rem;
  }

  .conjuntoss {
    padding: 48px 24px;
  }

  .tabela {
    grid-template-columns: repeat(2, 1fr);
    gap: 16px;
  }
}

@media (max-width: 480px) {
  .tabela {
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }

  .conjunto > img {
    height: 180px;
  }
}
</style>
