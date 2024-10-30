<script setup>

import { ref } from 'vue'

const Filmes = ref([])
const novoFilme = ref({
    nome:'',
    descricao:'',
    cinema:''
})

function salvar(){
    Filmes.value.push({ ...novoFilme.value });
    novoFilme.value = {nome:'', descricao:'', cinema:''};
}

function remover(i){
    Filmes.value.splice(i,1)
}

</script>

<template>
    <div>
        <label for="nome">Nome</label>
        <input id="nome" v-model="novoFilme.nome" type="text">

        <label for="duracao">Descrição</label>
        <input id="duracao" v-model="novoFilme.descricao" type="text">

        <label for="nota">Cinema</label>
        <input id="nota" v-model="novoFilme.cinema" type="text">

        <button @click="salvar">enviar</button>
    </div>
    <ul>
        <li v-for="filme, i in Filmes">
            Nome: {{ filme.nome }} Descrição: {{ filme.descricao }} Cinema: {{ filme.cinema }}
            <button @click="remover(i)">Remover</button>
        </li>
    </ul>
</template>