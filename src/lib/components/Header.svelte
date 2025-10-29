<script lang="ts">
  import Banner from "$lib/components/Banner.svelte";
  import Navbar from "./Navbar.svelte";

  export let styling: string = "";

  let mainWidth: string = "grid col-span-3 col-start-1 row-span-1 row-start-1";
</script>

<!-- <header
  class="{styling} sticky grid custom-grid-cols gap-x-clamp grid-rows-[1fr_auto] col-span-3 col-start-1 row-span-2 row-start-1 top-0 z-10 w-full h-20 md:h-18 backdrop-blur-sm"
>
  <Navbar />
</header> -->

<header
  id="mobile-header-content"
  class="fixed top-4 backdrop-blur-sm duration-100 ease-in-out w-screen z-10"
>
  <div
    class="flex flex-col font-sans 5 mx-auto z-50 navigation-width rounded-[64px] max-w-5xl border-zinc-200 border-b-2 shadow-sm p-2"
  >
    <div class="flex h-14 items-center justify-between py-2 pr-2 pl-4">
      <div class="flex items-center gap-2">
        <span
          data-state="closed"
          data-slot="context-menu-trigger"
          style="-webkit-touch-callout:none"
        >
          <a href="/#home" class="flex h-full items-center cursor-pointer">
            <img
              src="https://ik.imagekit.io/bip1v395ybp/Logo+Wordmark(Grey)_rvMOP40oz.png?updatedAt=1761358348126"
              alt="logo"
              class="h-12 w-auto"
            />
          </a></span
        >
      </div>
      <nav
        aria-label="Main navigation"
        class="hidden items-center gap-5 md:flex"
      >
        <ul class="flex items-center gap-4">
          <li>
            <button
              class="small transition-colors duration-200 cursor-pointer text-[16px] focus-visible:rounded-full focus-visible:ring-[2px] focus-visible:ring-white focus-visible:outline-none text-black-900"
              aria-expanded="false"
              aria-controls="header-product-menu">Discover</button
            >
          </li>
          <li>
            <button
              class="small transition-colors duration-200 cursor-pointer text-[16px] focus-visible:rounded-full focus-visible:ring-[2px] focus-visible:ring-white focus-visible:outline-none text-black-900"
              aria-expanded="false"
              aria-controls="header-community-menu">Media</button
            >
          </li>
          <li>
            <a
              class="small transition-colors duration-200 cursor-pointer text-[16px] focus-visible:rounded-full focus-visible:ring-[2px] focus-visible:ring-white focus-visible:outline-none text-black-900"
              href="/pricing">Events</a
            >
          </li>
          <li>
            <a
              class="small transition-colors duration-200 cursor-pointer text-[16px] focus-visible:rounded-full focus-visible:ring-[2px] focus-visible:ring-white focus-visible:outline-none text-black-900 plausible-event-name=click_link_download_header"
              href="/download">Giving</a
            >
          </li>
        </ul>
      </nav>
      <nav
        aria-label="Main navigation"
        class="hidden items-center gap-4 md:flex"
      >
        <ul class="flex items-center gap-3">
          <li>
            <a
              class="inline-flex items-center justify-center rounded-full whitespace-nowrap transition-all duration-200 disabled:pointer-events-none disabled:opacity-50 group bg-black text-white hover:bg-black-700 shadow-sm font-medium w-fit py-2 h-[36px] px-[14px] plausible-event-name=click_link_download_cta_header"
              href="/download"><span>Plan Your Visit</span></a
            >
          </li>
        </ul>
      </nav>
      <div class="flex items-center gap-2 pr-3 md:hidden">
        <button
          class="small text-black-900 hover:text-black-900 transition-colors duration-200"
          ><div class="relative h-6 w-6">
            <div class="absolute inset-0 cursor-pointer" style="opacity: 1;">
              <svg
                width="24"
                height="24"
                viewBox="0 0 24 24"
                fill="currentColor"
                xmlns="http://www.w3.org/2000/svg"
                class="text-black-900 h-6 w-6"
                ><path d="M4 7L20 7V5L4 5V7Z" fill="currentColor"></path><path
                  d="M4 19H20V17H4V19Z"
                  fill="currentColor"
                ></path><path
                  d="M4.00049 13.0005H20.0005V11.0005H4.00049V13.0005Z"
                  fill="currentColor"
                ></path></svg
              >
            </div>
            <div class="absolute inset-0 cursor-pointer" style="opacity:0">
              <svg
                width="24"
                height="24"
                viewBox="0 0 24 24"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
                class="text-black-900 h-6 w-6"
                ><path
                  d="M4.00049 13.0005H20.0005V11.0005H4.00049V13.0005Z"
                  fill="currentColor"
                ></path></svg
              >
            </div>
          </div></button
        >
      </div>
    </div>
  </div>
</header>
