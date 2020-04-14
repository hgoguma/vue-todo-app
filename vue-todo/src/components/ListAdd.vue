<template>
    <div>
        <!--텍스트 필드-->
        <v-textarea
            outlined
            v-model="memo"
            label="투두리스트를 입력해주세요."
            value=""
        >

        </v-textarea>
        <v-btn @click="listAdd">
            리스트 추가
        </v-btn>
        <!--추가 버튼-->

        투두 리스트 추가
    </div>
</template>

<script>
export default {
    data() {
        return {
            memo: null
        }
    },
    methods: {
        listAdd() {
            console.log('LisAdd listAdd func')
            if(this.memo === null) {
                alert('할 일을 입력해주세요')
            } else {
                this.$emit('listAdd', this.memo)
            }
        },
    }
}
</script>