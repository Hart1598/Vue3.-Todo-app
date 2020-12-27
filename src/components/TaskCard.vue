<template>
    <div class="task-card my-style">
        <div>
            <h4>{{model.title}}</h4>
            <p>{{model.description}}</p>
        </div>
        <div>
            <button @click="emitOnDone" v-if="!model.status">V</button>
            <button @click="emitOnRemove" v-else>X</button>
        </div>
    </div>
</template>

<script>
export default {
    emits: ['onDone', 'onRemove'],
    props:{
        model:{
            required: true,
            default:{ // Стандартная модель задачи
                id: 0,
                title: 'Create Video',
                description: 'And upload on youtube',
                status: false
            }
        }
    },
    setup(props, {emit}){
        const emitOnDone = () => {
            emit('onDone')
        }

        const emitOnRemove = () => {
            emit('onRemove')
        }

        return{
            emitOnDone,
            emitOnRemove
        }
    }
}
</script>

<style scoped>
    .task-card{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
</style>