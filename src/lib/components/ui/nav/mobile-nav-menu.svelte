<script lang="ts">
  import { fly } from "svelte/transition";
  import { quadInOut } from "svelte/easing";

  import NavItemList from "./nav-item-list.svelte";
  import JoinSocialList from "./join-social-list.svelte";
  const flyTransition = { y: -8, duration: 200, easing: quadInOut };
</script>

<div
  transition:fly={flyTransition}
  class="bg-card absolute top-0 left-0 z-40 w-full rounded-b-3xl pt-[72px] ease-in-out"
>
  <!-- we have our nav item list and join social lists -->
  <ul class="flex w-full flex-col space-y-5 py-4 pl-8">
    <NavItemList />
  </ul>

  <div
    class="xs:justify-start xs:space-x-4 xs:px-8 xs:pb-6 flex justify-between space-x-1 px-4 py-4"
  >
    <JoinSocialList />
  </div>
</div>
