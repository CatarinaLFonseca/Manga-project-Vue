<template>
    <div id="lista">
        <section>
            <article>
                <h1>Lista de Mangás</h1>
                    <ul>
                        <div class="grid-lista">
                            <button id="add" @click="showModal"><svg-icon type="mdi" :path="pathPlus"></svg-icon></button>
                            <AddManga :visible="isModalVisible" @close="isModalVisible = false">
                                <form @submit.prevent="salvarManga">
                                <h2>Adicione Mangás</h2>
                                <p>É possível adicionar mangás a lista, desde que preencha alguns campos abaixo:</p>
                                <input v-model="nome" type="text"
                                class="form-element" placeholder="Nome do Mangá" required>
                                <select class="form-element" v-model="opçoesStatus" id="Status" required>
                                    <option value="0">Selecione um status</option>
                                    <option value="1">Completo</option>
                                    <option value="2">Em Andamento</option>
                                </select>
                                <input type="file" id="mangafile" @change="salvarCapa" required>
                                <input type="submit" value="Salvar" id="check">
                                </form>
                            </AddManga>
                            <li class="grid-manga" v-for="(manga, i) in lista" :key="i">
                                <div id="nav">
                                    <span @click="mangaEdit(i)" class="options"><svg-icon type="mdi" :path="pathEdit"></svg-icon></span>
                                    <span @click="mangaDeleted(i)" class="options"><svg-icon id="del" type="mdi" :path="pathdelet"></svg-icon></span>
                                </div>
                                <img :src="manga.capa" alt="capa fairy tail">
                                <h2>{{ manga.nome }}</h2>
                                <p>{{ manga.status ? 'completo' : 'em andamento' }}</p>
                                </li>
                        </div>                        
                    </ul>
            </article>
        </section>
    </div>
</template>

<script>
import AddManga from './AddManga.vue'
import SvgIcon from '@jamescoyle/vue-icon'
import { mdiPlus } from '@mdi/js'
import { mdiDeleteForeverOutline } from '@mdi/js'
import { mdiPencilOutline } from '@mdi/js'

export default {
    components: {AddManga, SvgIcon},

    data() {
        return {  
            pathPlus: mdiPlus,  
            pathdelet: mdiDeleteForeverOutline,
            pathEdit: mdiPencilOutline,       
            nome: '',
            opçoesStatus: 0,
            capa: '',
            isModalVisible: false,
            isEdit: false,
            mangaIndex: null,
            lista: [
                {
                    capa: 'imagens/capa-fairy-tail.jpe',
                    nome: 'Fairy Tail',
                    status: true 
                },
                {
                    capa: 'imagens/capa-angel-beats.jpe',
                    nome: 'Angel Beats',
                    status: true 
                },
                {
                    capa: 'imagens/capa-another.jpe',
                    nome: 'Another',
                    status: true 
                },
                {
                    capa: 'imagens/capa-tokyo.jpe',
                    nome: 'Tokyo Ghoul: Re',
                    status: true 
                },
                {
                    capa: 'imagens/capa-naruto.jpe',
                    nome: 'Naruto',
                    status: true 
                },
                {
                    capa: 'imagens/capa-re.zero.jpe',
                    nome: 'Re: Zero',
                    status: true 
                },
                {
                    capa: 'imagens/capa-chainsaw.jpe',
                    nome: 'Chainsaw',
                    status: false 
                },
                {
                    capa: 'imagens/capa-magi.jpe',
                    nome: 'Magi',
                    status: true 
                },
                {
                    capa: 'imagens/capa-naruto-shipp.jpe',
                    nome: 'Naruto Shippuden',
                    status: true 
                },
                {
                    capa: 'imagens/capa-one-piece.jpe',
                    nome: 'One Piece',
                    status: false
                },
                {
                    capa: 'imagens/capa-kimi.jpe',
                    nome: 'Kimi ni Todoke',
                    status: true 
                },
                {
                    capa: 'imagens/capa-dragon-ball.jpe',
                    nome: 'Dragon Ball',
                    status: true 
                }
            ]
        }
    },
     methods: {
        mangaEdit(i){
            this.showModal()
            this.isEdit = true
            this.mangaIndex = i
            this.nome = this.lista[i].nome
            this.opçoesStatus = this.lista[i].status ? 1 : 2

        },
        mangaDeleted(i) {
            console.log(i)
            console.log(this.lista)
            this.lista.splice(i, 1)
        },
        showModal() {
            this.isModalVisible = true;
            this.nome = ''
            this.capa = ''
            this.opçoesStatus = 0
            this.isEdit = false
        },
        salvarManga() {
            if(+this.opçoesStatus === 0) {
                alert('Selecione um status')
                return
            }
            const status = +this.opçoesStatus === 1 ? true : false
            const manga = {
                capa: this.capa,
                nome: this.nome,
                status
            }
            if (this.isEdit) {
                this.lista[this.mangaIndex].capa = manga.capa
                this.lista[this.mangaIndex].nome = manga.nome
                this.lista[this.mangaIndex].status = manga.status
            } else {
                this.lista.unshift(manga)
            }
            
            this.isModalVisible = false
        },
        salvarCapa(event) {
            const file = event.target.files[0];
            const reader = new FileReader();
            reader.onload = (e) => {
                this.capa = e.target.result;
            };
            reader.readAsDataURL(file);

        }
    }
}
</script>

<style>
#add {
    background-color: rgba(125, 164, 187, 0.562);
    width: 150px;
    height: 150px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    margin: auto;
}

#lista {
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: rgba(125, 164, 187, 0.452);
    margin: 0px 20px;
    padding: 15px;
    padding-top: 0px;
    border: 1px solid rgba(0, 0, 0, 0.432);
    border-radius: 10px;
    box-shadow: 1px 1px 1px 1px rgba(0, 0, 0, 0.267);
}

section > article > h1 {
    text-align: center;
    font-size: 3em;
    font-family: 'gibi preto';
    margin-top: 20px;
    margin-bottom: 20px;
}

.grid-lista {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;
    width: 80%;
}

.grid-manga {
    position: relative;
}

section > article > ul > div > li {
    background-color:  rgba(125, 164, 187, 0.562);
    margin: auto;
    padding: 20px;
    padding-top: 0px;
    padding-bottom: 30px;
    list-style-type: none;
    border-radius: 10px;
    border: 1px solid rgba(0, 0, 0, 0.199);
}

ul > div > li:hover {
    background-color: rgba(240, 183, 225, 0.205);
    transition: 1s;
}

section > article > ul > div > li > img {
    width: 240px;
    height: 340px;
    border-radius: 10px;
    
}

section > article > ul > div > li > h2  {
    text-align: center;
}

section > article > ul > div > li > p {
    text-align: center;
    margin-top: 5px;
}

#nav {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    margin: 6px 0px 6px 0px;
    background-color: #cacaf16e;
    border: 1px solid #0000004d;
    border-radius: 10px;
}

.options {
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.9rem;
    font-weight: bold;
    height: 20px;
    width: 20px;
    margin: 5px;
    border-radius: 10px;
    color: #595757;
}

.options:hover,
.options:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}

#del {
    align-self: center;
}

@media screen and (max-width: 1475px) {
    .grid-lista {
    grid-template-columns: repeat(3, 1fr);
   }
}

@media screen and (max-width: 1160px) {
   .grid-lista {
    grid-template-columns: repeat(2, 1fr);
   }
    
}

@media screen and (max-width: 800px) {
   .grid-lista {
    grid-template-columns: repeat(1, 1fr);
   }
    
}

</style>