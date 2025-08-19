<script lang="ts">
  export let video: string;
  export let size: string;
</script>

<section data-background-video={video} data-background-size="cover">
  {#if size === "contain"}
    <div class="video-container">
      <div class="blur-layer"></div>
      <!-- svelte-ignore a11y_media_has_caption -->
      <video class="foreground-video" src={video}></video>
    </div>
  {/if}
  <div class="slot-container">
    <slot />
  </div>
</section>

<style>
  section {
    position: relative;
    width: 100%;
    height: 100%;
  }

  /* Container für den Slot - zentriert über allen Schichten */
  .slot-container {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 10; /* Über allen anderen Schichten */
  }
  /* Container für das Bild ohne Blurr-Effekt */
  .video-container {
    position: absolute;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    filter: none; /* Hebt den Blurr-Effekt des Body-Elements für diesen Container auf */
  }

  /* Transparentes Blur-Layer zwischen Hintergrund und Vordergrund */
  .blur-layer {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(255, 255, 255, 0.1); /* Transparenter weißer Hintergrund */
    backdrop-filter: blur(10px); /* Blur-Effekt */
    z-index: 1; /* Zwischen Hintergrund (z-index: 0) und Vordergrund (z-index: 2) */
  }

  /* Das zentrierte Bild in voller Höhe */
  .foreground-video {
    position: relative;
    z-index: 2; /* Über dem Blur-Layer */
    height: 100%;
    max-height: 100%; /* Stellt sicher, dass das Bild die volle Höhe des Containers einnimmt */
    width: auto; /* Die Breite wird automatisch angepasst, um das Seitenverhältnis zu erhalten */
    display: block; /* Entfernt den standardmäßigen Freiraum unterhalb von Inline-Elementen */
    object-fit: contain; /* Stellt sicher, dass das Bild in den Container passt, ohne beschnitten zu werden */
  }
</style>
