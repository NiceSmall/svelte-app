<script>
  import { createEventDispatcher } from 'svelte'
  import ProgressBar from './ProgressBar.svelte'
  const dispatch = createEventDispatcher()
  const totalSeconds = 3;
  let secondsLeft = totalSeconds;
  $: progress = ((totalSeconds - secondsLeft) / totalSeconds) * 100
  let isRunning = false
  function startTimer() {
    isRunning = true
    const timer = setInterval(() => {
      secondsLeft -= 1;    
      if (secondsLeft == 0) {
        clearInterval(timer)
        isRunning = false
        secondsLeft = totalSeconds
        dispatch('end', 'end timer')
      }
    }, 100);
  }
</script>
<p>进度：{secondsLeft}</p>
<p>进度：{progress}</p>
<ProgressBar {progress} />

<button disabled={isRunning} on:click={startTimer}>开始</button>