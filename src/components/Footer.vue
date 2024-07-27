<template>
  <footer>
        <p>
            Site criado por <a href="https://github.com/CatarinaLFonseca/" target="_blank"><strong>Catarina Fonseca</strong></a> inspirado no projeto do <a href="https://github.com/becoolxz" target="_blank"><strong>Lucas Ribeiro</strong></a>.
        </p>
    </footer>
</template>

<script>
export default {

}
</script>

<style>
footer {
    background-color: rgba(125, 164, 187, 0.452);
    text-align: center;
    margin: 10px 19px;
    padding: 10px;
    border-radius: 10px;
    border: 1px solid rgba(0, 0, 0, 0.411);
    box-shadow: 1px 1px 1px 1px rgba(0, 0, 0, 0.205);
}

footer > p {
    font-size: 1em;
}

footer > p > a {
    color: rgb(0, 0, 0);
    text-decoration: none;
    padding: 3px;
    
}

footer > p > a:hover {
    background-color: rgba(240, 183, 225, 0.603);
    transition: 1s;
    border-radius: 8px;
}


</style>