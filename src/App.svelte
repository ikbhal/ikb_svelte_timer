<script>
	import { tweened } from 'svelte/motion';
  let original = 5 * 60; // TYPE NUMBER OF SECONDS HERE
	let timer = tweened(original)

  // ------ dont need to modify code below
  import Typewriter from "svelte-typewriter";
  setInterval(() => {
    if ($timer > 0) $timer--;
  }, 1000);

  $: minutes = Math.floor($timer / 60);
  $: minname = minutes > 1 ? "mins" : "min";
  $: seconds = Math.floor($timer - minutes * 60)
</script>

<main>
  <div class="flex">

    <img src="https://sveltesociety.dev/logo.svg" alt="logo" width="100" />
    <div class="title">SVELTE SOCIETY DAY</div>
  </div>

  {#if timer < 1}
    <Typewriter loop>
      <h1>Starting soon....</h1>
    </Typewriter>
  {:else}
<h1>We will be back in <span class="mins">{minutes}</span>{minname} 
	
	<span class="secs">{seconds}</span>s!</h1>
<progress value={$timer/original}></progress>
  {/if}
  <!-- 	feel free to modify this text!! -->
  <ul>
    <li>
      <strong>Next talk</strong>
      : Effective Transitioning (Andrew Smith)
    </li>
    <li>
      <strong>Then</strong>
      : A Framework for the Modern Storyteller (Robert Hall)
    </li>
    <li>
      <strong>Last</strong>
      : Svelte FAQ (Rich Harris)
    </li>
  </ul>

  <footer>
    <p>
      <em>
        See this REPL at
        <a
          href="https://svelte.dev/repl/42ed4a09041e4e39b2f43f798eb898cb?version=3.21.0"
        >
          https://bit.ly/2zxmJiu
        </a>
      </em>
    </p>
    <p>
      <em>
        All Talks and Demos/Resources at
        <a href="https://bit.ly/3bDwMAA">https://bit.ly/3bDwMAA</a>
      </em>
    </p>
  </footer>
</main>

<style>
  main {
    width: 600px;
    margin: 0 auto;
  }
	
	progress {
		display: block;
		width: 100%;
	}
	.mins {
		color: darkgoldenrod;
	}
	.secs {
		color: darkgoldenrod;
	}
  footer {
    margin-top: 3rem;
  }
  li {
    margin-bottom: 1rem;
  }
  .flex {
    display: flex;
    align-items: center;
  }
  .title {
    font-size: 2rem;
    font-weight: bold;
  }
</style>
