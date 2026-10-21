<script>
    let hajok = [4, 3, 3, 2, 2, 2, 1, 1, 1, 1]
    let display = Array.from({length: 10}).map(()=>Array(10).fill(""))
    let palya = Array.from({length: 10}).map(()=>Array(10).fill(0))
    hajok.forEach((v, j) => {
        let ok = false
        while (!ok) {
            if (Math.random()>0.5) { //vízszintes irány
                let x = Math.round(Math.random() * (9 - v - 2)) + 1
                let y = Math.round(Math.random() * (9 - 2)) + 1
                ok = true
                for (let i = 0; i < v; i++) {
                    if (palya[y][x + i]) ok = false
                }
                if (ok) {
                    palya[y - 1][x - 1] = 1
                    palya[y][x - 1] = 1
                    palya[y + 1][x - 1] = 1
                    for (let i = 0; i < v; i++) {
                        palya[y - 1][x + i] = 1
                        palya[y][x + i] = j + 2
                        palya[y + 1][x + i] = 1
                    }
                    palya[y - 1][x + v] = 1
                    palya[y][x + v] = 1
                    palya[y + 1][x + v] = 1
                }
            } else { //függőleges irány
                let x = Math.round(Math.random() * (9 - 2)) + 1
                let y = Math.round(Math.random() * (9 - v - 2)) + 1
                ok = true
                for (let i = 0; i < v; i++) {
                    if (palya[y + i][x]) ok = false
                }
                if (ok) {
                    palya[y - 1][x - 1] = 1
                    palya[y - 1][x] = 1
                    palya[y - 1][x + 1] = 1
                    for (let i = 0; i < v; i++) {
                        palya[y + i][x - 1] = 1
                        palya[y + i][x] = j + 2
                        palya[y + i][x + 1] = 1
                    }
                    palya[y + v][x - 1] = 1
                    palya[y + v][x] = 1
                    palya[y + v][x + 1] = 1
                }
            }
        }
    })
    console.log(palya)
</script>
<h1>Torpedo</h1>
<table>
    <tbody>
    {#each display as row, j}
    <tr>
        {#each row as cell, i}
            <td on:click={() => {
                display[j][i] = palya[j][i]
            }} class="c{display[j][i]}">
                {cell>-1?["", "⬯", "①", "②", "③", "④", "⑤", "⑥", "⑦"][cell]:""}
            </td>
        {/each} 
    </tr>
    {/each}    
    </tbody>
</table>
<style>
    h1 {
        text-align: center;
    }
    table {
        margin: 0 auto;
        border-spacing: 6px;
    }
    td {
        width: 30px;
        height: 30px;
        background-color: aqua;
        border-radius: 5px;
        box-shadow: 1px 2px 3px gray;
        text-align: center;
        cursor: pointer;
    }
    td.c0 {
        background-color: beige;
    }
    td.c1 {
        background-color: rgb(217, 216, 188);
    }
    td.c2 {
        background-color: rgb(127, 255, 163);
    }
    td.c3 {
        background-color: rgb(255, 185, 127);
    }
    td.c4 {
        background-color: rgb(240, 127, 255);
    }
    td.c5 {
        background-color: rgb(255, 127, 189);
    }
    td.c6 {
        background-color: rgb(215, 147, 45);
    }
    td.c7 {
        background-color: rgb(131, 127, 255);
    }
    td.c8 {
        background-color: rgb(29, 152, 57);
    }
    
</style>