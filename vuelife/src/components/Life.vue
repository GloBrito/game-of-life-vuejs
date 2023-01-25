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

function contaVizinhosVivos(i,y,grid){
    const deltaCelulaContigua = [
        [-1,-1], [-1,0], [-1,-1],
        [0,-1], [0,1],
        [1,-1], [1,0], [1,1],
    ]
    let coordVizinhos = []
    for (let k = 0; k < deltaCelulaContigua.length; k++){
        coordVizinhos.push([i + deltaCelulaContigua[k][0], y + deltaCelulaContigua[k][0]])
    }
    console.log(i, y, grid)
    return 0
}
function _nextState(grid){
    const [x, z] = [grid.length, grid[0].length]
    let newGrid = new Array(x)
    for (let i = 0; i < x; i++){
        newGrid[i] = new Array(z).fill(0)
    }
    for(let i = 0; i < x; i++){
        for (let y = 0; y < z; y++){
           let vizinhosVivos = contaVizinhosVivos(i,y,grid)
            if(grid[i][y] == 1){
                if (vizinhosVivos == 2 || vizinhosVivos == 3){
                    newGrid[i][y] = 1
                } else {
                    newGrid[i][y] = 0
                }    
            } else {
                if (vizinhosVivos == 3){
                    newGrid[i][y] = 1
                } else {
                    newGrid[i][y] = 0
                }
            }
        }
    }    
    return newGrid
}

export default ({
    name: 'Life',
    data() {
    return {
        grid: [ //matriz inicial
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
    nextStep() {
        this.grid = _nextState(this.grid)
    },    
},
methods: {
    nextStep(){
            this.grid = _nextState(this.grid)
        }
    },
    mounted(){
        setInterval (() => {
            this.nextStep()
        }, 300)
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
.vivo{
    background-color: yellow;
}
</style>