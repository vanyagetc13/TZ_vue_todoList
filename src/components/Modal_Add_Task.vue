<template>
    <div class="wrapper" v-if="mAT">
        <div class="modal">
            <h3>Создание задачи</h3>
            <form class="form">
                <div>
                    <h4>Что нужно сделать?</h4>
                    <MyInput class="mt-10" placeholder="Опишите задачу..." v-model="description"/>
                </div>
                <div class="btns mt-10">
                    <WarningButton @click="closeModal">
                        Отмена
                    </WarningButton>
                    <PrimaryButton class="fz-1" @click="taskCreate">
                        Создать
                    </PrimaryButton>
                </div>
            </form>
        </div>
    </div>
</template>

<script>
import MyInput from "@/components/UI/MyInput.vue"
import PrimaryButton from "@/components/UI/PrimaryButton.vue"
import WarningButton from "@/components/UI/WarningButton.vue"
export default {
    components: {
        MyInput,
        PrimaryButton, WarningButton
    },
    data() {
        return {
            description: "",
        }
    },
    props: {
        mAT: {
            type: Boolean,
            required: true
        }
    },
    methods:{
        taskCreate (e) {
            e.preventDefault()
            const todo = {
                text: this.description
            }
            this.$emit('addTodo', todo)
        },
        closeModal(e) {
            e.preventDefault()
            // this.$emit('close')
            console.log(this.description);
        }
    }
}
</script>

<style scoped>
.wrapper {
    background-color: rgba(63, 63, 63, 0.4);
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 99999;
}

.modal {
    min-width: 500px;
    min-height: 300px;
    background-color: #fff;
    border-radius: 10px;

    padding: 20px;
    display: flex;
    flex-direction: column;
    gap: 10px;
}

.modal h3 {
    color: #29A19C;
}

.mt-10 {
    margin-top: 10px;
}

.btns{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.btns * {
    font-size: 0.9em;
}

.form {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    flex: 1;
}
</style>