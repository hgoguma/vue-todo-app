<template>
    <div>
        <v-card
            class="pa-3"
            v-for="(list, index) in todoList"
            :key="index"
        >
            <p>{{list.memo}}</p>
            <v-btn fab text small color="black"><i class="fas fa-check"></i></v-btn>
            <v-btn fab text small color="blue"><i class="fas fa-redo-alt"></i></v-btn>
            <v-btn fab text small color="red"><i class="fas fa-trash-alt"></i></v-btn>
        </v-card>
    </div>
</template>

<script>
export default {
    props: ['todoList']
}
</script>