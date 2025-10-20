<!-- ignore how ugly this file is pls I'm rushing and am very sorry... -->

<script lang="ts">
  import { page } from "$app/state";
  import { afterNavigate } from "$app/navigation";
  import { fade } from "svelte/transition";
  import { Icon } from "$lib/components/ui/icon";
  import { ChevronDown } from "@lucide/svelte";
  import Join from "./join.svelte";
  import NavItemList from "./nav-item-list.svelte";
  import MobileNavButton from "./mobile-nav-button.svelte";
  import MobileNavMenu from "./mobile-nav-menu.svelte";
  let open = false;
  let scrollY: number;

  afterNavigate((navigation: import("@sveltejs/kit").AfterNavigate) => {
    if (navigation.type === "link") {
      open = false;
    }
  });

  const firstLetterUpperCase = (word: string) => {
    return word.charAt(1).toUpperCase() + word.slice(2);
  };

  const chevronDownTransition = (open: boolean) => {
    return ["transition-all duration-200", open ? "rotate-180" : ""];
  };
</script>

<!-- desktop -->
{#if page.url.pathname === "/"}
  <div class="pointer-events-none absolute z-50 h-full">
    <nav
      class={[
        "pointer-events-auto sticky top-0 hidden w-screen flex-row items-center justify-between rounded-b-3xl p-3 transition-all md:flex",
        scrollY > 100 ? "bg-background/100" : "bg-background/0",
      ]}
    >
      <a href="/" class="pb-1">
        <Icon
          variant="aunsw"
          size={40}
          fill={scrollY > 100 ? "var(--foreground)" : "white"}
          class="transition-all"
        />
      </a>

      <ul class="flex flex-row space-x-9">
        <NavItemList {scrollY} />
      </ul>

      <Join />
    </nav>
  </div>
{:else}
  <nav
    class="bg-background sticky top-0 hidden flex-row items-center justify-between rounded-b-3xl p-3 md:flex"
  >
    <a href="/" class="pb-1">
      <Icon variant="aunsw" size={40} fill="var(--foreground)" />
    </a>

    <ul class="flex flex-row space-x-9">
      <NavItemList />
    </ul>

    <Join />
  </nav>
{/if}

<!-- mobile -->
{#if page.url.pathname === "/"}
  <div class="pointer-events-none absolute z-50 h-full">
    <nav
      class={[
        "pointer-events-auto sticky top-0 flex w-screen flex-col gap-y-4 rounded-b-3xl px-4 transition-all md:hidden",
        scrollY > 100 ? "bg-background/100" : "bg-background/0",
      ]}
    >
      <MobileNavButton bind:open>
        <a href="/" class="pb-1">
          <Icon
            variant="aunsw"
            size={36}
            fill={scrollY > 100 || open ? "var(--foreground)" : "white"}
            class="transition-all"
          />
        </a>

        {#if !open}
          <span transition:fade={{ duration: 100 }} class="text-3xl"
            >{firstLetterUpperCase(page.url.pathname)}</span
          >
        {/if}

        <div class="flex items-center pr-1">
          <ChevronDown
            class={chevronDownTransition(open)}
            size={36}
            color={scrollY > 100 || open ? "var(--foreground)" : "white"}
          />
        </div>
      </MobileNavButton>

      {#if open}
        <MobileNavMenu />
      {/if}
    </nav>
  </div>
{:else}
  <nav
    class="bg-background sticky top-0 flex flex-col gap-y-4 rounded-b-3xl px-4 md:hidden"
  >
    <MobileNavButton bind:open>
      <a href="/" class="pb-1">
        <Icon variant="aunsw" size={36} fill="var(--foreground)" />
      </a>

      {#if !open}
        <span transition:fade={{ duration: 100 }} class="text-3xl"
          >{firstLetterUpperCase(page.url.pathname)}</span
        >
      {/if}

      <div class="flex items-center pr-1">
        <ChevronDown class={chevronDownTransition(open)} size={36} />
      </div>
    </MobileNavButton>

    {#if open}
      <MobileNavMenu />
    {/if}
  </nav>
{/if}

<svelte:window bind:scrollY />
