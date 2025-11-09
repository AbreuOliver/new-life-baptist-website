<script lang="ts">
  import BentoSection from "$lib/components/BentoSection.svelte";
  import HeroOrbit from "$lib/components/HeroOrbit.svelte";

  import "../global.css";
</script>

<div id="main" class="flex flex-col items-center space-y-0 grow min-h-40">
  <HeroOrbit
    title="A Christ-Centered Church"
    subtitle="A loving community of believers in White Marsh, Maryland that believes in the life-changing power of Jesus"
    cta={{ label: "Plan Your Visit", href: "/plan-your-visit" }}
    secondary={{ label: "Learn More", href: "/about" }}
  />

  <div class="w-screen bg-sky-500 text-white relative mt-20">
    <div class="max-w-5xl mx-auto min-h-60 px-6 space-y-4 py-20">
      <!-- <div
        class="mx-auto mt-6 grid w-full max-w-5xl gap-6 pb-12 sm:grid-cols-2"
      >

        <div
          class="rounded-xl border border-zinc-200 bg-white p-6 shadow-sm primary-serif"
        >
          <h2 class="mb-4 text-lg font-semibold text-zinc-900">
            Service Times
          </h2>
          <ul class="space-y-4 text-zinc-700">
            <li class="flex items-center justify-between">
              <span class="text-left">Sunday<br />Bible Study</span>
              <time class="text-right text-zinc-600">10:00 AM</time>
            </li>
            <li class="flex items-center justify-between">
              <span class="text-left">Sunday Worship</span>
              <span class="text-right text-zinc-600"
                >11:00 AM<br />&amp; 6:30 PM</span
              >
            </li>
            <li class="flex items-center justify-between">
              <span class="text-left">Wednesday<br />Prayer Meeting</span>
              <time class="text-right text-zinc-600">7:00 PM</time>
            </li>
          </ul>
        </div>

        <div
          class="rounded-xl border border-zinc-200 bg-white p-6 shadow-sm primary-serif"
        >
          <h2 class="mb-4 text-lg font-semibold text-zinc-900">Contact Info</h2>
          <ul class="space-y-4 text-zinc-700">
            <li>
              <a
                href="https://www.google.com/maps/search/?api=1&amp;query=5975+US+70+East+La+Grange,+NC+28551"
                target="_blank"
                rel="noopener noreferrer"
                class="group inline-flex items-start gap-3 hover:underline"
              >
                <svg
                  class="mt-0.5 h-5 w-5 text-zinc-500"
                  viewBox="0 0 16 16"
                  fill="currentColor"
                  ><path
                    fill="currentColor"
                    fill-rule="evenodd"
                    d="m7.539 14.841l.003.003l.002.002a.755.755 0 0 0 .912 0l.002-.002l.003-.003l.012-.009a6 6 0 0 0 .19-.153a15.6 15.6 0 0 0 2.046-2.082C11.81 11.235 13 9.255 13 7A5 5 0 0 0 3 7c0 2.255 1.19 4.235 2.292 5.597a15.6 15.6 0 0 0 2.046 2.082l.189.153zM8 8.5a1.5 1.5 0 1 0 0-3a1.5 1.5 0 0 0 0 3"
                    clip-rule="evenodd"
                  ></path></svg
                >
                <span>5975 US 70 East<br />La Grange, NC 28551</span>
              </a>
            </li>
            <li>
              <a
                href="tel:+12525662170"
                class="group inline-flex items-center gap-3 hover:underline"
              >
                <svg
                  class="h-5 w-5 text-zinc-500"
                  viewBox="0 0 20 20"
                  fill="currentColor"
                  ><path
                    fill="currentColor"
                    fill-rule="evenodd"
                    d="M2 3.5A1.5 1.5 0 0 1 3.5 2h1.148a1.5 1.5 0 0 1 1.465 1.175l.716 3.223a1.5 1.5 0 0 1-1.052 1.767l-.933.267c-.41.117-.643.555-.48.95a11.54 11.54 0 0 0 6.254 6.254c.395.163.833-.07.95-.48l.267-.933a1.5 1.5 0 0 1 1.767-1.052l3.223.716A1.5 1.5 0 0 1 18 15.352V16.5a1.5 1.5 0 0 1-1.5 1.5H15c-1.149 0-2.263-.15-3.326-.43A13.02 13.02 0 0 1 2.43 8.327A13 13 0 0 1 2 5z"
                    clip-rule="evenodd"
                  ></path></svg
                >
                <span>(252) 566-2170</span>
              </a>
            </li>
            <li>
              <a
                href="mailto:info@emmanuelbaptistnc.org"
                class="group inline-flex items-center gap-3 hover:underline"
              >
                <svg
                  class="h-5 w-5 text-zinc-500"
                  viewBox="0 0 20 20"
                  fill="currentColor"
                  ><path
                    fill="currentColor"
                    fill-rule="evenodd"
                    d="M2 5a1 1 0 0 1 1-1h14a1 1 0 0 1 1 1v10a1 1 0 0 1-1 1H3a1 1 0 0 1-1-1V5zm1 0v10h14V5H3z"
                    clip-rule="evenodd"
                  ></path>
                  <path fill="currentColor" d="M4 6.5l6 4l6-4V5l-6 4l-6-4v1.5z"
                  ></path>
                </svg>
                <span>info@emmanuelbaptistnc.org</span>
              </a>
            </li>
          </ul>
        </div>
      </div> -->
      <BentoSection />
    </div>
  </div>
</div>
