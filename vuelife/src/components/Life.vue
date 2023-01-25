<template>
    <div >
    <table>
        <tr v -for="line in grid" : key="line">
            <td></td>
            <td></td>
        </tr>
        <tr>
            <td class= "celula_viva"></td>
            <td></td>
        </tr>
    </table>
    </div>
</template>

<script>
export default{
    name: "Life",
    data() {
        return {
           grid: [
                [0, 0, 0, 0, 0, 0, 0, 0, 0, 0,],
                [0, 0, 0, 0, 0, 0, 0, 0, 0, 0,],
                [0, 0, 0, 0, 0, 0, 0, 0, 0, 0,],
                [0, 0, 0, 0, 0, 0, 0, 0, 0, 0,],
                [0, 0, 0, 0, 0, 0, 0, 0, 0, 0,],
                [0, 0, 0, 0, 0, 0, 0, 0, 0, 0,],
                [0, 0, 0, 0, 0, 0, 0, 0, 0, 0,],
                [0, 0, 0, 0, 0, 0, 0, 0, 0, 0,],
                [0, 0, 0, 0, 0, 0, 0, 0, 0, 0,],
                [0, 0, 0, 0, 0, 0, 0, 0, 0, 0,],
           ]
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