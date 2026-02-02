<!-- ignore how ugly this file is pls I'm rushing and am very sorry... -->

<script lang="ts">
  import { page } from "$app/state";
  import { afterNavigate } from "$app/navigation";
  import { quadInOut } from "svelte/easing";
  import { fade, fly } from "svelte/transition";
  import { Icon } from "$lib/components/ui/icon";
  import { Button } from "$lib/components/ui/button";
  import { ChevronDown } from "@lucide/svelte";
  import NavItem from "./nav-item.svelte";
  import Join from "./join.svelte";
  import JoinSocial from "./join-social.svelte";

  let open = false;
  let scrollY: number;

  afterNavigate((navigation: import("@sveltejs/kit").AfterNavigate) => {
    if (navigation.type === "link") {
      open = false;
    }
  });
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
        <NavItem href="/events" label="Events" {scrollY} />
        <NavItem href="/sponsors" label="Sponsors" {scrollY} />
        <NavItem href="/info" label="Info" {scrollY} />
        <NavItem href="/blog" label="Blog" {scrollY} />
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
      <NavItem href="/events" label="Events" />
      <NavItem href="/sponsors" label="Sponsors" />
      <NavItem href="/info" label="Info" />
      <NavItem href="/blog" label="Blog" />
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
      <button
        class="z-50 flex items-center justify-between py-4"
        onclick={() => (open = !open)}
      >
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
            >{page.url.pathname.charAt(1).toUpperCase() +
              page.url.pathname.slice(2)}</span
          >
        {/if}

        <div class="flex items-center pr-1">
          <ChevronDown
            class={["transition-all duration-200", open ? "rotate-180" : ""]}
            size={36}
            color={scrollY > 100 || open ? "var(--foreground)" : "white"}
          />
        </div>
      </button>

      {#if open}
        <div
          transition:fly={{ y: -8, duration: 200, easing: quadInOut }}
          class="bg-card absolute top-0 left-0 z-40 w-full rounded-b-3xl pt-[72px] ease-in-out"
        >
          <ul class="flex w-full flex-col space-y-5 py-4 pl-8">
            <NavItem href="/events" label="Events" />
            <NavItem href="/sponsors" label="Sponsors" />
            <NavItem href="/info" label="Info" />
            <NavItem href="/blog" label="Blog" />
          </ul>

          <div
            class="xs:justify-start xs:space-x-4 xs:px-8 xs:pb-6 flex justify-between space-x-1 px-4 py-4"
          >
            <JoinSocial
              icon="rubric"
              label="Rubric"
              href="https://campus.hellorubric.com/?s=12432"
              big={true}
            />
            <JoinSocial
              icon="discord"
              label="Discord"
              href="https://discord.gg/aunsw"
            />
            <JoinSocial
              icon="instagram"
              label="Instagram"
              href="https://instagram.com/animeunsw"
            />
            <JoinSocial
              icon="facebook"
              label="Facebook"
              href="https://www.facebook.com/unswanime/"
            />
            <JoinSocial
              icon="xiaohongshu"
              label="RedNote"
              href="https://discord.gg/aunsw"
            />
          </div>
        </div>
      {/if}
    </nav>
  </div>
{:else}
  <nav
    class="bg-background sticky top-0 flex flex-col gap-y-4 rounded-b-3xl px-4 md:hidden"
  >
    <button
      class="z-50 flex items-center justify-between py-4"
      onclick={() => (open = !open)}
    >
      <a href="/" class="pb-1">
        <Icon variant="aunsw" size={36} fill="var(--foreground)" />
      </a>

      {#if !open}
        <span transition:fade={{ duration: 100 }} class="text-3xl"
          >{page.url.pathname.charAt(1).toUpperCase() +
            page.url.pathname.slice(2)}</span
        >
      {/if}

      <div class="flex items-center pr-1">
        <ChevronDown
          class={[
            "transition-transform duration-200",
            open ? "rotate-180" : "",
          ]}
          size={36}
        />
      </div>
    </button>

    {#if open}
      <div
        transition:fly={{ y: -8, duration: 200, easing: quadInOut }}
        class="bg-card absolute top-0 left-0 z-40 w-full rounded-b-3xl pt-[72px] ease-in-out"
      >
        <ul class="flex w-full flex-col space-y-5 py-4 pl-8">
          <NavItem href="/events" label="Events" />
          <NavItem href="/sponsors" label="Sponsors" />
          <NavItem href="/info" label="Info" />
          <NavItem href="/blog" label="Blog" />
        </ul>

        <div
          class="xs:justify-start xs:space-x-4 xs:px-8 xs:pb-6 flex justify-between space-x-1 px-4 py-4"
        >
          <JoinSocial
            icon="rubric"
            label="Rubric"
            href="https://campus.hellorubric.com/?s=12432"
            big={true}
          />
          <JoinSocial
            icon="discord"
            label="Discord"
            href="https://discord.gg/aunsw"
          />
          <JoinSocial
            icon="instagram"
            label="Instagram"
            href="https://instagram.com/animeunsw"
          />
          <JoinSocial
            icon="facebook"
            label="Facebook"
            href="https://www.facebook.com/unswanime/"
          />
          <JoinSocial
            icon="xiaohongshu"
            label="RedNote"
            href="https://discord.gg/aunsw"
          />
        </div>
      </div>
    {/if}
  </nav>
{/if}

<svelte:window bind:scrollY />
