<script lang="ts">
  export let frame: string;
</script>

<section data-background-iframe={frame} data-preload>
  <slot />
</section>
