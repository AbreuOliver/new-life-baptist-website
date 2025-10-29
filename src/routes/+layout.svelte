<script lang="ts">
  import dayjs from "dayjs";
  import PromoModal from "$lib/components/PromoModal.svelte";
  import Banner from "$lib/components/Banner.svelte";
  import MyModal from "$lib/components/MyModal.svelte";
  import "../global.css";
  import Header from "$lib/components/Header.svelte";
  // import SiteHeader from '$lib/components/SiteHeader.svelte';
  // import SiteFooter from '$lib/components/SiteFooter.svelte'

  let currentYear: number = new Date().getFullYear();
  let isMenuOpen: boolean = false;

  function toggleMenu() {
    isMenuOpen = !isMenuOpen;
    console.log("Menu State:", isMenuOpen);
  }

  const targetDate = dayjs("2025-08-25");
  const lastDate = dayjs("2025-09-10");
  const currentDate = dayjs();

  // Calculate days until revival
  const daysUntilRevival = targetDate.diff(currentDate, "day");

  // Check if we're before the end date
  const isBeforeEnd = currentDate.isBefore(lastDate);

  const startDate = dayjs("2025-10-08").startOf("day"); // go-live date
  const endDate = dayjs("2025-10-26").endOf("day"); // inclusive through the day
  const now = dayjs();

  // Reuse the name, but make it correct and self-contained:
  const isLive = !now.isBefore(startDate) && !now.isAfter(endDate);

  // Flowbite modal open state
  let promoOpen = false;
  if (isLive) promoOpen = true; // show immediately while live

  let isCoolModalOpen = false;
</script>

<Header />
<main class="grow min-h-[60vh]">
  <slot />
</main>
