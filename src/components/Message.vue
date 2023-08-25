<template>
    <div class="message-container">
        <p>{{ msg }}</p>
    </div>
</template>

<script>
export default{
    name: "Message",
    props: {
        msg:String
    }
}
</script>
<style scoped>
    .message-container{
        color: #0a7400;
        background-color: #9bffb9;
        border: 2px solid #0a7400;
        border-radius: 5px;
        padding: 10px;
        max-width: 400px;
        margin: 30px auto;
    }

</style>