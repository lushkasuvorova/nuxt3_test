<template>
    <div class="form" id="form">
        <div :id="i" v-for="(item, i) in items" :key="i" class="reply">
            <Img class="user" src="/konuhov.jpg" height="50px" /><br>
            {{ item }}
            <button class="icon_reply" type="button" @click="reply(i)"><Img src="/icons24.png" /></button><br>
            <div v-for="(comment, j) in comments[i]" :key="j" class="comment">
                <Img class="user" src="/konuhov.jpg" height="50px" /><br>
                {{ comment }}
            </div>
        </div>
        <label>Оставить отзыв</label>
        <textarea @blur="back()" ref="input" rows="10" required cols="50" placeholder="..." />
        <button class = "button" @click="add()">Отправить</button>
    </div>
</template>
<script>
export default {
    el: "#form",
    data() {
        return {
            items: [],
            comments: [],
            reply_id: "пусто"
        };
    },
    methods: {
        add: function () {
            if (this.$refs.input.value) {
                if (this.reply_id == "пусто") {
                    this.items.push(this.$refs.input.value)
                    const n = this.items.length-1
                    this.comments[n]=[]
                } else {
                    const n = this.reply_id
                    this.comments[n].push(this.$refs.input.value)
                    this.reply_id="пусто"
                }
                this.$refs.input.value = ''
            }
        },
        reply: function (i) {
            this.reply_id = i
            this.$refs.input.focus()
        },
        back: function() {
            if (!this.$refs.input.value)this.reply_id="пусто"
        }
    }
}
</script>
<style>
.comment {
    margin-left: 1.5em;
    margin-top: 1.5em;
    margin-bottom: 1em;
}

.reply {
    margin-top: 1.5em;
    margin-bottom: 1em;  
}

.icon_reply {
    border: unset; 
}

.form {
    margin-top: 1.5em;
}

.user {
    border-radius: 25px;
}

div {
    white-space: pre-line;
}

label {
    display: block;
    margin-bottom: 1em;
    font-weight: 700;
    font-family: Padauk, sans-serif;
}

textarea {
    width: 100%;
    margin-top: 0.5em;
}

.button {
    border: unset;
    background: #79b791;
    color: #230c0f;
    font-weight: 700;
    padding: 1em 2.5em;
    margin-top: 1em;
}
</style>