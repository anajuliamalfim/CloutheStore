<template>
    <footer>
        <div class="geral">
            <div class="social">
                <p>Loja de Roupas</p>
                <ul>
                    <li>
                        <a href="#"><img src="../../public/footerIMG/facebook.png" alt=""></a>
                    </li>
                    <li>
                        <a href="#"><img src="../../public/footerIMG/instagram.png" alt=""></a>
                    </li>
                    <li>
                        <a href="#"><img src="../../public/footerIMG/twitter.png" alt=""></a>
                    </li>
                </ul>
            </div>
            <div class="about">
                <div class="contact">
                    <p>Contato</p>
                    <ul>
                        <li>
                            <img src="../../public/footerIMG/telefone.png" alt="">
                            <p>+55 (47) 98267-6921</p>
                        </li>
                        <li>
                            <img src="../../public/footerIMG/relogio.png" alt="">
                            <p>8h às 17h - Seg a Sab</p>
                        </li>
                        <li>
                            <img src="../../public/footerIMG/gmail.png" alt="">
                            <p>contato@maresia.com</p>
                        </li>
                    </ul>
                </div>
                <ul class="payment">
                    <li>
                        <img src="../../public/footerIMG/paypal.png" alt="">
                    </li>
                    <li>
                        <img src="../../public/footerIMG/cartao.png" alt="">
                    </li>
                    <li>
                        <img src="../../public/footerIMG/visa.png" alt="">
                    </li>
                </ul>
            </div>
        </div>
        <hr>
        <p class="copyright">&copy; Alguns direitos reservados. Loja de Roupas 2025.</p>
    </footer>
</template>

<style scoped>
footer {
    background-color: #f8f4ef;
    padding: 40px 8%;
    color: #6b4f2a;
    font-family: Arial, Helvetica, sans-serif;
}

.geral {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    flex-wrap: wrap;
    gap: 30px;
}

.social p,
.contact > p {
    font-size: 1.3rem;
    font-weight: 600;
    margin-bottom: 15px;
}

.social ul,
.contact ul,
.payment {
    list-style: none;
    padding: 0;
    margin: 0;
}

.social ul {
    display: flex;
    gap: 15px;
}

.social ul li img {
    width: 35px;
    height: 35px;
    transition: transform 0.3s;
}

.social ul li img:hover {
    transform: scale(1.1);
}

.about {
    display: flex;
    flex-direction: column;
    gap: 25px;
}

.contact ul li {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 12px;
}

.contact ul li img {
    width: 22px;
    height: 22px;
}

.contact ul li p {
    margin: 0;
}

.payment {
    display: flex;
    gap: 15px;
}

.payment li img {
    width: 50px;
    height: auto;
}

hr {
    margin: 30px 0 15px;
    border: none;
    border-top: 1px solid #d6c5ad;
}

.copyright {
    text-align: center;
    font-size: 0.9rem;
    color: #8a6b45;
}

/* Responsividade */
@media (max-width: 768px) {
    .geral {
        flex-direction: column;
        align-items: center;
        text-align: center;
    }

    .contact ul li {
        justify-content: center;
    }

    .payment {
        justify-content: center;
    }
}
</style>
