<template>
    <div>
        <form>
            <input v-model="todo">
            <button type="button" @click="sendTodo">追加</button>
        </form>
        <ul v-for="item in items">
            <li @click="doneTodo(item)">
                <span>
                    status : {{ item.status }}
                </span>
                <s v-if="item.status == 'done'">
                    {{ item.text }}
                </s>
                <span v-else>
                    {{ item.text }}
                </span>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                todo : "",
                items : []
            }
        },
        methods: {
            sendTodo() {
                this.items.push({
                    text : this.todo,
                    status : 'todo'
                })
                this.todo = ""
            },
            doneTodo(item) {
                item.status === 'done' ? item.status = 'todo' : item.status = 'done'
            }
        }
    }
</script>

<style>

</style>