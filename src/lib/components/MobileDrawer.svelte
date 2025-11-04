<script lang="ts">
  import { createEventDispatcher } from "svelte";
  import { fade, scale } from "svelte/transition";

  export let isMenuOpen = false;

  const dispatch = createEventDispatcher();
  const close = () => dispatch("close");

  const links = [
    { href: "/#about", label: "about" },
    { href: "/#media", label: "media" },
    { href: "/#events", label: "events" },
    { href: "/#give", label: "give" },
  ];
  const linkClass = "block hover:text-sky-700 capitalize";
</script>

{#if isMenuOpen}
  <div
    aria-hidden="true"
    on:click={close}
    in:fade={{ duration: 600 }}
    out:fade={{ duration: 600 }}
  />

  <div class="fixed inset-0 z-50 grid place-items-center pointer-events-none">
    <nav
      class="absolute pointer-events-auto mx-auto top-24 w-[85%] max-w-md rounded-3xl border border-zinc-200 bg-white p-8 shadow-2xl shadow-zinc-600/10
             dark:border-neutral-700 dark:bg-neutral-800 dark:shadow-none"
      role="dialog"
      aria-modal="true"
      in:scale={{ duration: 600, start: 0.95 }}
      out:scale={{ duration: 600, start: 0.98 }}
    >
      <ul
        class="flex flex-col gap-6 primary-serif italic text-xl text-zinc-700 dark:text-neutral-200"
      >
        {#each links as { href, label }}
          <li><a {href} class={linkClass} on:click={close}>{label}</a></li>
        {/each}
      </ul>
    </nav>
  </div>
{/if}
