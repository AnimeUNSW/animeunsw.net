<script lang="ts">
  export let open: boolean = false;
</script>

<button
  class="z-50 flex items-center justify-between py-4"
  onclick={() => (open = !open)}
>
  <slot />
</button>
