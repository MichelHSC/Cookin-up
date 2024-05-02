<script>
import Tag from './Tag.vue';

export default{
    name: 'IngredienteSelecionavel',
    components:{
        Tag
    },
    props:{
        ingrediente:{ type: String, required:true}
    },
    data(){
        return{
            selecionado: false
        }
    },
    methods:{
        selected(){
            this.selecionado = !this.selecionado

            if(this.selecionado){
                this.$emit('adicionarIngrediente', this.ingrediente);
            }else if(!this.selecionado){
                this.$emit('removerIngrediente',this.ingrediente)
            }
        }
    },
    emits: ['adicionarIngrediente','removerIngrediente']
}

</script>

<template>
    <button class="ingrediente" @click="selected">
        <Tag :texto="ingrediente" :ativa="selecionado"/>
    </button>


</template>

<style scoped>
.ingrediente{
    cursor: pointer;
}

</style>