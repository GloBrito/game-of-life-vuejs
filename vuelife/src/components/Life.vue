<template>
    <div>
        <h1>Hello Life {{ msg }}</h1>
    <table>
        <tr>
            <td>1</td>
            <td>2</td>
        </tr>
        <tr>
            <td>3</td>
            <td>4</td>
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