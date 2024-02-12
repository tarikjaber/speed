<script>
  import Counter from './lib/Counter.svelte'
  
  let pastScores = []
  let score = 1000

  let startTime = new Date()
  
  function updateTime() {
    let currTime = new Date()
    
    let passed = Math.floor(+currTime / 1000) - Math.floor(+startTime / 1000)
    score = 1000 - passed
  }
  
  function calculateScore(pastScores, score) {
    let sumPastScores = pastScores.reduce((a, b) => a + b, 0)
    let sumScoresTotal = sumPastScores + score
    let numScores = pastScores.length + 1

    return Math.floor(sumScoresTotal / numScores)
  }

  setInterval(updateTime, 333);
  
  let done = () => {
    startTime = new Date()
    pastScores = [...pastScores, score]
  }
</script>

<h1>Score: {calculateScore(pastScores, score)}</h1>
<h1>{score}</h1>
<Counter on:done={done}/>

<style>

</style>
