<template>
    <template v-if="!isEdit">
        <p style="font-size: 22px; padding: 30px">{{ text }}</p><br>
        <button @click="$emit('remove', id)">Удалить</button>
        <button @click="edit">Изменить</button><br>
    </template>
    <template v-else>
        <input v-model="newText" type="text"><br>
        <button @click="save">Сохранить</button>
    </template>

</template>
<script>

export default {
    emits: ['remove', 'change'],
    props: {
        id: Number,
        text: String,
    },
    data() {
        return {
            isEdit: false,
            newText: this.text,
        }
    },
    methods: {
        edit() {
            this.isEdit = true
        },
        save() {
            this.isEdit = false
            this.$emit('change', this.id, this.newText)
        }
    }
}
</script>