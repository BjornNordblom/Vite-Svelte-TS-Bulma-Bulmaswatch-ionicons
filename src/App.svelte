<script lang="ts">
  import svelteLogo from "./assets/svelte.svg";
  import Counter from "./lib/Counter.svelte";
</script>

<section>
  <!-- Hero content: will be in the middle -->
  <div class="hero">
    <div class="hero-body">
      <div class="container">
        <div class="container">
          <h1 class="title">Search</h1>
          <h2 class="subtitle">Tip: Use +task, +log and +step as keywords to only search those areas.</h2>
          <p>
            <input class="input" type="text" placeholder="Input" />
          </p>
        </div>
      </div>
    </div>
  </div>
</section>

<main>
  <div class="columns">
    <div class="column is-2">
      <aside class="menu section">
        <p class="menu-label">Group of links</p>
        <ul class="menu-list">
          <li>
            <a href="#somesubpage"> Some subpage </a>
          </li>
        </ul>
      </aside>
    </div>
    <div class="column">
      <section class="section" id="mainSection">
        <div>
          <a href="https://vitejs.dev" target="_blank" rel="noreferrer">
            <img src="/vite.svg" class="logo" alt="Vite Logo" />
          </a>
          <a href="https://svelte.dev" target="_blank" rel="noreferrer">
            <img src={svelteLogo} class="logo svelte" alt="Svelte Logo" />
          </a>
        </div>
        <h1>Vite + Svelte + TS + Bulma + Bulmaswatches + ionicons</h1>
        <p>
          Check out <a href="https://github.com/sveltejs/kit#readme" target="_blank" rel="noreferrer">SvelteKit</a>, the
          official Svelte app framework powered by Vite!
        </p>
        <p>
          Check out <a href="https://jenil.github.io/bulmaswatch" target="_blank" rel="noreferrer">Bulmaswatch</a>, some
          very nice templates!
        </p>
        <p>
          Check out <a href="https://ionic.io/ionicons" target="_blank" rel="noreferrer">ionicons</a>, really sharp and
          clean icons!
        </p>
        <hr />
        <div class="columns">
          <div class="column">
            <div class="card">
              <Counter />
            </div>
          </div>
          <div class="column">
            <div class="card">
              <h1>Card 2</h1>
            </div>
          </div>
          <div class="column">
            <div class="card">
              <h1>Card 3</h1>
            </div>
          </div>
        </div>
      </section>
    </div>
    <div class="column is-2" />
  </div>
</main>

<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #000);
  }
</style>
