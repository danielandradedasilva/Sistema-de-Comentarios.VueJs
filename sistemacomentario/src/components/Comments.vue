<template>
     <div class="container">
        <h1 style="text-align: center; margin-top: 35px;">Comentários</h1>
       <FormTodo v-on:add-todo="addComment"></FormTodo>
        <hr>
        <div class="list-group">
            <div class="list-group-item" v-for="(comment,index) in allComments" v-bind:key="index">
                <span class="coment_autor">Autor: <strong>{{comment.name}}</strong></span>
                <p>Comentário: <strong>{{comment.message }}</strong></p>
                <div>
                    <a href="#" title="excluir" v-on:click.prevent="removeComment(index)">Excluir</a>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

import FormTodo from './FormTodo';

export default{
components:{
    FormTodo
},
data() {
        return {
            comments: []
        }
    },
    methods:{
        addComment(comment){
            this.comments.push(comment);
        },

        removeComment(index) {
            this.comments.splice(index, 1);
        }
    },
    computed: {
        allComments() {
            return this.comments.map(comment => ({
                ...comment,
                name: comment.name.trim() === '' ? 'Anônimo' : comment.name
            }))
        }
    }
}

</script>

 
