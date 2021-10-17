<template>
     <div class="form-todo form-group">
            <p>
                <input placeholder="nome" name="autor" class="form-control" type="text" v-model="name">
            </p>
            <p>
                <textarea name="mensagem" id="mensagem" class="form-control" placeholder="Comentário" v-model="message">
                </textarea>
            </p>
            <button v-on:click="addComent" type="submit" class="btn btn-primary">Comentar</button>
        </div>
</template>

<script>
export default {
    data(){
        return{
            name: '',
            message: ''
        }
    },
        methods: {
            addComent() {
            if (this.message.trim() === '') {
                return alert('Faça um comentário!');
            }

            this.$emit('add-todo', {
               name: this.name,
               message: this.message
            });

            this.name = '';
            this.message = '';
        }
    }
}
</script>