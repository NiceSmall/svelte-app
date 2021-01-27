<script>
  import Timer from './Timer.svelte'
  import HowTo from './HowTo.svelte'
  let audio;
  function timerEnds(e) {
    console.log(e);
    audio.play()
  }
</script>

<h1>当前字体</h1>
<h1>Current Font</h1>

<Timer on:end={timerEnds} />
<HowTo />

<audio bind:this={audio}>
  <source src="snip.wav" />
</audio>