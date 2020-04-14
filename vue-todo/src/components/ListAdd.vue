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
        <!--추가 버튼-->
        <v-btn v-if="mode === 'add'" @click="listAdd">
            리스트 추가
        </v-btn>
        <v-btn v-if="mode === 'edit'" @click="listEdit">
            리스트 수정
        </v-btn>
    </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
    data() {
        return {
            memo: null,
            index: null,
            mode: 'add',
        }
    },
    created() {
        eventBus.$on('listEdit', (memo, index) => {
            this.memo = memo;
            this.index = index;
            this.mode = 'edit';
        }) 
    },
    methods: {
        listAdd() {
            if(this.memo === null) {
                alert('할 일을 입력해주세요')
            } else {
                this.$emit('listAdd', this.memo)
                this.memo = null
            }
        },
        listEdit() {
            if(this.memo === null) {
                alert('할 일을 입력해주세요')
            } else {
                this.$emit('listEdit', this.memo, this.index);
                this.memo = null;
                this.mode = 'add';
            }
        }
    }
}
</script>