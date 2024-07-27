<template>
  <header>
        <nav>
            <a href="">Home</a>
            <a href="">Mangás</a>
            <a href="">Nossa História</a>
            <a href="">Contato</a>
            <a href="">Localização</a>
        </nav>
        <img src="imagens/tituloPagina.png" alt="Logo da pagina" id="logo">
    </header>
</template>

<script>
export default {

}
</script>

<style>
header {
    display: flex;
    flex-direction: column;
    align-items: center;
}
header > nav {
    font-weight: bold;
    font-size: 18px;  
    background-color: rgba(125, 164, 187, 0.452);
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
    margin: auto;
    box-shadow: 1px 1px 1px rgba(0, 0, 0, 0.199);
    display: flex;
    flex-direction: row;
}
header > nav > a {
    color: rgba(0, 0, 0, 0.849);
    text-decoration: none;
    padding: 20px 35px;
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
}
nav > a:hover {
    background-color: rgba(240, 183, 225, 0.603);
    transition: 1s;
}

img#logo {
    margin-top: 30px;
    width: 380px;
}

@media screen and (max-width: 778px) {
    header > nav > a {
        font-size: 15px;
        padding: 20px 15px;
    }
}

</style>