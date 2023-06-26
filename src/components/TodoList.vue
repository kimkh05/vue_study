<template>
    <div>
        <transition-group name="list" tag="ul">
            <li v-for="(todoItem, index) in this.storedTodoItems" v-bind:key="todoItem.item" class="shadow">
                <i class="checkBtn fas fa-check" v-bind:class="{ checkBtnCompleted: todoItem.completed }"
                    v-on:click="toggleComplete({ todoItem, index })"></i>
                <span v-bind:class="{ textCompleted: todoItem.completed }">{{ todoItem.item }}</span>
                <span class="removeBtn" v-on:click="removeTodo({ todoItem, index })">
                    <i class="fas fa-trash-alt"></i>
                </span>
            </li>
        </transition-group>
    </div>
</template>

<script>
import { mapMutations, mapGetters } from 'vuex';

export default {
    methods: {
        ...mapMutations({
            // span 태그에서 사용하는 함수名 : '호출되는 뮤테이션名'
            // 호출하는 단에서 (여기서는 span 태그쪽) 넘겨주는 매개변수가 있다면
            // 암묵적으로 mapMutations 에서 자동으로 넘겨준다.
            // 근데 보면 원래 mutation 호출할 때 객체로 넘겨줬으니까 html 쪽도 수정이 필요하다
            removeTodo: 'removeOneItem',
            toggleComplete: 'toggleOneItem'
        }),
    },
    computed: {
        ...mapGetters(['storedTodoItems']),
    }
}
</script>