<template>
    <div>
        <v-card
            class="pa-3"
            :class="{'done' : list.status === 'done'}"
            v-for="(list, index) in todoList"
            :key="index"
        >
            <p>{{list.memo}}</p>
            <v-btn 
                v-if="list.status === 'created'"
                @click="$emit('statusControl', index, 'done')"
                fab text small color="green">
                <i class="fas fa-check"></i>
            </v-btn>
            <v-btn
                v-if="list.status === 'done'"
                @click="$emit('statusControl', index, 'created')" 
                fab text small color="blue">
                <i class="fas fa-redo-alt"></i>
            </v-btn>
            <v-btn
                @click="$emit('listDelete', index)"
                fab text small color="red">
                <i class="fas fa-trash-alt"></i>
            </v-btn>
        </v-card>
    </div>
</template>

<script>
export default {
    props: ['todoList']
}
</script>

<style scoped>
    .done {
        background-color: rgba(0, 0, 0, 0.1);
    }
    .done p {
        text-decoration: line-through;
        color: rgba(0, 0, 0, 0.5)
    }
</style>