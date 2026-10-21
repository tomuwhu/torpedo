<script>
    let hajok = [4, 3, 3, 2, 2, 2, 1]
    let palya = Array.from({length: 10}).map(()=>Array(10).fill(0))
    hajok.forEach((v, j) => {
        let ok = false
        while (!ok) {
            if (Math.random()>0.5) { //vízszintes irány
                let x = Math.round(Math.random() * (9 - v - 2)) + 1
                let y = Math.round(Math.random() * (9 - 2)) + 1
                console.log("vízszintes", v, x, y);
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
                console.log("függőleges", v, x, y);
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
