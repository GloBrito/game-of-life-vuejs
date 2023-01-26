<template>
    <div>
        <table>
            <tr v-for="(line, i) in grid" :key="i">
                <td v-for="(celula, y) in line" :key="y" :class="{celulaViva: celula==1}"></td>
            </tr>
        </table>
    </div>    
</template>

<script>


function contaVizinhosVivos(i,y,grid){
    const [x, z] = [grid.length, grid[0].length]
    const deltaCelulaContigua = [
        [-1,-1], [-1,0], [-1,-1],
        [0,-1], [0,1],
        [1,-1], [1,0], [1,1],
    ]
    let coordVizinhos = []
    for (let k = 0; k < deltaCelulaContigua.length; k++){
        coordVizinhos.push([i + deltaCelulaContigua[k][0], y + deltaCelulaContigua[k][1]])
    }
    let coordVizinhosVivos = coordVizinhos.filter((e) => e[0] >= 0 && e[0] < x && e[1] < z && grid[e[0]][e[1]] == 1)
    return coordVizinhosVivos.length
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
                } 
                else {
                    newGrid[i][y] = 0
                }
            }
        }
    }    
    return newGrid
}

export default {
    name: 'Life',
    data() {
        return {
            grid: [ //matriz inicial
                [0,0,0,0,1,0,0,0,0,0,1,0,0,0,0],
                [0,0,0,0,1,0,0,0,0,0,1,0,0,0,0],
                [0,0,0,0,1,1,0,0,0,1,1,0,0,0,0],
                [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],
                [1,1,1,0,0,1,1,0,1,1,0,0,1,1,1],
                [0,0,1,0,1,0,1,0,1,0,1,0,1,0,0],
                [0,0,0,0,1,1,0,0,0,1,1,0,0,0,0],
                [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],
                [0,0,0,0,1,1,0,0,0,1,1,0,0,0,0],
                [0,0,1,0,1,0,1,0,1,0,1,0,1,0,0],
                [1,1,1,0,0,1,1,0,1,1,0,0,1,1,1],
                [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],
                [0,0,0,0,1,1,0,0,0,1,1,0,0,0,0],
                [0,0,0,0,1,0,0,0,0,0,1,0,0,0,0],
                [0,0,0,0,1,0,0,0,0,0,1,0,0,0,0],
            ]
        }
    },
    methods: {
        nextStep(){
            this.grid = _nextState(this.grid)
    },
    },
    mounted(){
        setInterval(() => {
            this.nextStep()
        }, 1000)
    }
  }
</script>

<style>
table, th, td {
    padding: .7em;
    margin: 300px;
    border: 1px solid;
}
td {
    width: 30px;
    height: 30px;
}

.celulaViva {
    background-color: #9c27b0;
}
</style>