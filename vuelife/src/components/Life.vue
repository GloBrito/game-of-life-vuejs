<template>
    <div >
        <h1>Hello Life {{ msg }}</h1>
    <table>
        <tr>
            <td class= "celula_viva"></td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td></td>
        </tr>
    </table>
    </div>
</template>

<script>
export default{
    data() {
        return {
            msg: '{{vai aparecer uma mensagem aqui}}'
        }
    }
}
</script>

<style>
table, th, td {
    border: 1px solid
}
td{
    width: 30px;
    height: 30px;
}
.celula_viva{
    background-color: red;
}
</style>