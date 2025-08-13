<template>
    <footer class="footer">
        <div class="footer-content">
            <div class="logo-section">
                <h2 class="logo">CLIMAJÁ</h2>
                <p class="subtitle">
                    Imagine a bright yellow sun behind a blue-white cloud.</p>
            </div>

            <div class="apps-section">
                <span>Baixe os apps</span>
                <button class="btn-climatempo">Localclima</button>

                <a href="https://play.google.com/store/apps/details?id=seuapp" target="_blank" class="icon android">
                    <i class="fab fa-android"></i>
                </a>
                <a href="https://apps.apple.com/app/idseuapp" target="_blank" class="icon apple">
                    <i class="fab fa-apple"></i>
                </a>
            </div>

            <div class="social-section">
                <span>Developer</span>
                <div class="social-icons">
                    <a href="https://facebook.com/" target="_blank" class="icon facebook">
                        <i class="fab fa-facebook-f"></i>
                    </a>
                    <a href="https://twitter.com/" target="_blank" class="icon twitter">
                        <i class="fab fa-twitter"></i>
                    </a>
                    <a href="https://linkedin.com/in/josevaldomoreira" target="_blank" class="icon linkedin">
                        <i class="fab fa-linkedin-in"></i>
                    </a>
                    <a href="https://instagram.com/josevaldomr" target="_blank" class="icon instagram">
                        <i class="fab fa-instagram"></i>
                    </a>
                    <a href="https://youtube.com/@josevaldomoreira-une5772" target="_blank" class="icon youtube">
                        <i class="fab fa-youtube"></i>
                    </a>
                </div>
            </div>
        </div>

        <p class="copyright">&copy; 2025 Localclima. Todos os direitos reservados.</p>

    </footer>

</template>

<script setup>
// Nenhum script necessário por enquanto
</script>

<style scoped>
.footer {
    background-color: #3b3b3b;
    color: white;
    padding: 20px 40px;
    display: table-column;
    justify-content: center;
}

.footer-content {
    max-width: 1200px;
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
}

.logo-section {
    display: flex;
    flex-direction: column;
}

.logo {
    margin: 0;
    font-size: 20px;
    letter-spacing: 1px;
}

.subtitle {
    font-size: 12px;
    color: #ccc;
    margin-top: 4px;
}

.apps-section {
    display: flex;
    align-items: center;
    gap: 10px;
}

.btn-climatempo {
    background-color: #007ac2;
    border: none;
    color: white;
    padding: 6px 12px;
    border-radius: 20px;
    cursor: pointer;
    font-weight: bold;
}

.social-section {
    display: flex;
    align-items: center;
    gap: 10px;
}

.social-icons {
    display: flex;
    gap: 8px;
}

/* Ícones gerais */
.icon {
    display: inline-flex;
    justify-content: center;
    align-items: center;
    width: 36px;
    height: 36px;
    border-radius: 50%;
    font-size: 16px;
    color: white;
    text-decoration: none;
    background-color: #222;
}

/* Ícones específicos */
.icon.android {
    background-color: #3ddc84;
}

.icon.apple {
    background-color: #000;
}

.facebook {
    background-color: #3b5998;
}

.twitter {
    background-color: #1da1f2;
}

.linkedin {
    background-color: #0077b5;
}

.instagram {
    background: radial-gradient(circle at 30% 30%, #feda75, #d62976, #962fbf);
}

.youtube {
    background-color: red;
}

/* Rodapé legal (copyright) */
.copyright {
    /* background-color: #222; */
    text-align: center;
    width: 100%;
    margin-top: 20px;
    font-size: 12px;
    color: #aaa;
}
</style>
