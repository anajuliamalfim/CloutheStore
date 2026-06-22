<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const pesquisa = ref('')
const router = useRouter()

function pesquisar() {
  if (!pesquisa.value) return

  router.push({
    path: '/',
    query: { q: pesquisa.value }
  })
}
</script>
<template>
    <header>
        <RouterLink to="/"><div class="logotipo">
            <img src="/public/otherIMG/logo.png" alt="">
        </div></RouterLink>
        <div class="barrapesquisa">
        <input
            type="text"
            v-model="pesquisa"
            placeholder="Pesquisar"
            @keyup.enter="pesquisar"
        >

        <button @click="pesquisar">
            <img src="/headerIMG/procurar.png" alt="Pesquisar">
        </button>
    </div>
        <div class="opcoes">
            <ul>
                <li>Termos</li>
                <li>Equipe</li>
                <li>Envio</li>
                <li>Devoluções</li>
            </ul>
        </div>
        <div class="direcionamentos">
            <ul>
                <li>
                    <RouterLink to="/cart"><img src="../../public/headerIMG/carrinho.png"
                            alt="icone de direcionamento para o carrinho de compras"></RouterLink>
                </li>
                <hr>
                <li>
                    <a href=""><img src="../../public/headerIMG/coracao2.png"
                            alt="icone de direcionamento para os produtos favoritos"></a>
                </li>
                <hr>
                <li>
                    <a href=""><img src="../../public/headerIMG/perfil.png"
                            alt="icone de direcionamento para a página do usuário"></a>
                </li>
            </ul>
        </div>
    </header>
</template>
<style scoped>
header {
    width: 100%;
    padding: 15px 5%;
    background-color: #f8f4ef;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 25px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}

/* Logo */
.logotipo img {
    height: 70px;
    width: auto;
    display: block;
}

/* Barra de pesquisa */
.barrapesquisa {
    flex: 1;
    max-width: 500px;
    display: flex;
    align-items: center;
    border: 2px solid #c7a777;
    border-radius: 30px;
    overflow: hidden;
    background-color: #fff;
}

.barrapesquisa input {
    flex: 1;
    border: none;
    outline: none;
    padding: 12px 18px;
    font-size: 1rem;
    background: transparent;
}

.barrapesquisa button {
    border: none;
    background-color: #c7a777;
    padding: 12px 18px;
    cursor: pointer;
    transition: 0.3s;
}

.barrapesquisa button:hover {
    background-color: #a88454;
}

.barrapesquisa button img {
    width: 18px;
    height: 18px;
}

/* Menu */
.opcoes ul {
    display: flex;
    gap: 20px;
    list-style: none;
    padding: 0;
    margin: 0;
}

.opcoes li {
    cursor: pointer;
    font-weight: 500;
    color: #6b4f2a;
    transition: 0.3s;
}

.opcoes li:hover {
    color: #c7a777;
}

/* Ícones */
.direcionamentos ul {
    display: flex;
    align-items: center;
    gap: 15px;
    list-style: none;
    padding: 0;
    margin: 0;
}

.direcionamentos li {
    display: flex;
    align-items: center;
}

.direcionamentos img {
    width: 28px;
    height: 28px;
    transition: transform 0.3s;
}

.direcionamentos img:hover {
    transform: scale(1.15);
}

.direcionamentos hr {
    width: 1px;
    height: 25px;
    border: none;
    background-color: #d1b48c;
}

/* Responsivo */
@media (max-width: 1024px) {
    header {
        flex-wrap: wrap;
        justify-content: center;
    }

    .barrapesquisa {
        order: 3;
        width: 100%;
        max-width: 100%;
    }

    .opcoes ul {
        flex-wrap: wrap;
        justify-content: center;
    }
}

@media (max-width: 768px) {
    .opcoes {
        display: none;
    }

    .logotipo img {
        height: 55px;
    }

    .direcionamentos img {
        width: 24px;
        height: 24px;
    }
}
</style>
