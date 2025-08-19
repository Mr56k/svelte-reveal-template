<script lang="ts">
  import Reveal from "reveal.js";
  import Markdown from "reveal.js/plugin/markdown/markdown";
  import Highlight from "reveal.js/plugin/highlight/highlight";
  import Notes from "reveal.js/plugin/notes/notes";
  import { onMount } from "svelte";

  import "reveal.js/dist/reveal.css";
  import "reveal.js/dist/reset.css";
  import "reveal.js/dist/theme/dracula.css";
  import "reveal.js/plugin/highlight/monokai.css";
  import Presentation from "./presentation.svelte";

  onMount(() => {
    const deck = new Reveal({
      hash: true,
      hashOneBasedIndex: true,
      controls: true,
      progress: true,
      overview: true,
      touch: true,
      autoPlayMedia: null,
      defaultTiming: 10,
      transitionSpeed: "fast",
    });

    deck.initialize({
      width: "100%",
      height: "100%",
      margin: 0,
      minScale: 1,
      maxScale: 1,
      plugins: [Markdown, Highlight, Notes],
    });
  });
</script>

<div class="reveal">
  <div class="slides">
    <Presentation />
  </div>
</div>
