<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" @keyup.enter="addTodo">
        <span class="addContainer" @click="addTodo">
            <i class="fas fa-plus addBtn"></i>
        </span>
        <AlertModal v-if="showModal" @close="showModal = false">
            <h3>
                경고!!
                <i class="closeModalBtn fas fa-times" @click="showModal = false"></i>
            </h3>

            <div>
                null은 저장할 수 없습니다!!
            </div>
        </AlertModal>
    </div>
</template>

<script>
import AlertModal from './modal/AlertModal.vue';

export default {
    name: "TodoInput",

    data() {
        return {
            newTodoItem: '',
            showModal: false,
        }
    },

    methods: {
        addTodo() {
            if (this.newTodoItem !== '') {
                this.$store.commit('addOneItem', this.newTodoItem);
                this.clearInput();
            } else {
                this.showModal = true;
            }
        },
        clearInput() {
            this.newTodoItem = '';
        },
        closeModal() {
            this.showModal = false;
        }
    },

    components: {
        AlertModal
    }
}
</script>
