<script lang="ts">
  export let open: boolean = false;
</script>

<!-- our button container for hte mobile nav button -->
<button
  class="z-50 flex items-center justify-between py-4"
  onclick={() => (open = !open)}
>
  <slot />
</button>
