<template>
    <div>
        <table>
            <tr v-for="(line, i) in grid" :key="i">
                <td v-for="(celula, y) in line" :key="y" :class="{celulaViva: celula==1}"></td>
                <td></td>
            </tr>
        </table>
    </div>    
</template>

<script>
export default({
    name: 'Life',
    data() {
    return {
        grid: [
            [0,0,0,0,0,0,0,0,0],
            [0,0,0,0,0,0,0,0,0],
            [0,1,1,1,0,1,1,1,0],
            [1,0,0,0,1,0,1,0,1],
            [0,1,0,0,0,0,0,1,0],
            [0,0,1,0,0,0,1,0,0],
            [0,0,0,1,0,1,0,0,0],
            [0,0,0,0,1,0,0,0,0],
            [0,0,0,0,0,0,0,0,0],
            [0,0,0,0,0,0,0,0,0],
        ]
    }
},
methods: {
nextStep(){
    this.grid = [
            [0,0,0,0,0,0,0,0,0],
            [0,0,0,0,0,0,0,0,0],
            [0,1,1,1,0,1,1,1,0],
            [1,0,0,0,1,0,1,0,1],
            [0,1,0,0,0,0,0,1,0],
            [0,0,1,0,0,0,1,0,0],
            [0,0,0,1,0,1,0,0,0],
            [0,0,0,0,1,0,0,0,0],
            [0,0,0,0,0,0,0,0,0],
            [0,0,0,0,0,0,0,0,0],
        ]
    }    
},
mounted(){
    setInterval(() => {
        this.nextStep()
    }, 1000)
  }
})
</script>

<style>
table, th, td{
    border: 1px solid;
}
td {
    width: 30px;
    height: 30px;
}
.celulaViva{
    background-color: red;
}
</style>