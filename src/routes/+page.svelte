<script lang="ts">
  import SmallCalendar from "$lib/components/SmallCalendar.svelte";
  import HeroOrbit from "$lib/components/HeroOrbit.svelte";
  import PaperPage from "$lib/components/PaperPage.svelte";

  const orbitItems = [
    { ring: 1, angle: 15, src: "/avatars/a1.jpg", alt: "A1", size: "w-8 h-8" },
    {
      ring: 1,
      angle: 120,
      src: "src/lib/icons/Prayer.icon.svelte",
      alt: "Idea",
      size: "w-7 h-7",
    },
    { ring: 2, angle: 60, src: "/avatars/a2.jpg", alt: "A2", size: "w-9 h-9" },
    {
      ring: 2,
      angle: 210,
      src: "/icons/check.svg",
      alt: "Solved",
      size: "w-7 h-7",
    },
    {
      ring: 3,
      angle: -30,
      src: "/avatars/a3.jpg",
      alt: "A3",
      size: "w-10 h-10",
    },
    {
      ring: 3,
      angle: 160,
      src: "/icons/heart.svg",
      alt: "Likes",
      size: "w-7 h-7",
    },
    {
      ring: 4,
      angle: 95,
      src: "/avatars/a4.jpg",
      alt: "A4",
      size: "w-10 h-10",
    },
    {
      ring: 4,
      angle: -140,
      src: "/icons/sparkles.svg",
      alt: "Sparkles",
      size: "w-8 h-8",
    },
  ];

  import "../global.css";
  import Footer from "$lib/components/Footer.svelte";
  import Highlight from "$lib/components/Highlight.svelte";

  const yellow = "#f8db75";
  const green = "oklch(0.93 0.07 135)";
  const blue = "oklch(0.92 0.08 230)";
  const pink = "oklch(0.93 0.08 20)";

  const sc = "tracking-wide";
</script>

<div id="main" class="flex flex-col items-center space-y-0 grow min-h-40">
  <HeroOrbit
    title="A Christ-Centered Church"
    subtitle="A loving community of believers in White Marsh, Maryland that believes in the life-changing power of Jesus"
    cta={{ label: "Plan Your Visit", href: "/start" }}
    secondary={{ label: "Learn More", href: "/video" }}
    items={orbitItems}
  />

  <div class="mx-auto w-screen special-serif h-fit p-1 pb-40">
    <article class="mx-auto max-w-prose">
      <header class="mb-4">
        <h2 class="text-xl font-semibold tracking-wide">Psalm 119:9–16</h2>
        <!-- <p class="text-xs uppercase tracking-wider text-zinc-500">
          NASB (excerpt)
        </p> -->
      </header>

      <!-- verses -->
      <ol
        role="list"
        class="divide-y divide-zinc-200 rounded-md border border-zinc-200 bg-white/70 shadow-sm"
      >
        <!-- v9 -->
        <li class="grid grid-cols-[2rem,1fr] gap-x-3 p-3 leading-relaxed">
          <span
            class="col-[1] select-none text-right font-medium tabular-nums text-zinc-500"
            >9</span
          >
          <p class="col-[2]">
            How can a young man keep his way pure?<br />
            <span class="text-zinc-700"
              >By keeping it according to Your word.</span
            >
          </p>
        </li>

        <!-- v10 -->
        <li class="grid grid-cols-[2rem,1fr] gap-x-3 p-3 leading-relaxed">
          <span
            class="col-[1] select-none text-right font-medium tabular-nums text-zinc-500"
            >10</span
          >
          <p class="col-[2]">
            With all my heart I have sought You;<br />
            Do not let me wander from Your commandments.
          </p>
        </li>

        <!-- v11 -->
        <li class="grid grid-cols-[2rem,1fr] gap-x-3 p-3 leading-relaxed">
          <span
            class="col-[1] select-none text-right font-medium tabular-nums text-zinc-500"
            >11</span
          >
          <p class="col-[2]">
            I have treasured Your word in my heart,<br />
            So that I may not sin against You.
          </p>
        </li>

        <!-- v12 -->
        <li class="grid grid-cols-[2rem,1fr] gap-x-3 p-3 leading-relaxed">
          <span
            class="col-[1] select-none text-right font-medium tabular-nums text-zinc-500"
            >12</span
          >
          <p class="col-[2]">
            Blessed are You, Lord;<br />
            Teach me Your statutes.
          </p>
        </li>

        <!-- v13 -->
        <li class="grid grid-cols-[2rem,1fr] gap-x-3 p-3 leading-relaxed">
          <span
            class="col-[1] select-none text-right font-medium tabular-nums text-zinc-500"
            >13</span
          >
          <p class="col-[2]">
            With my lips I have told of<br />
            All the ordinances of Your mouth.
          </p>
        </li>

        <!-- v14 -->
        <li class="grid grid-cols-[2rem,1fr] gap-x-3 p-3 leading-relaxed">
          <span
            class="col-[1] select-none text-right font-medium tabular-nums text-zinc-500"
            >14</span
          >
          <p class="col-[2]">
            I have rejoiced in the way of Your testimonies,<br />
            <span class="text-zinc-700">As much as in all riches.</span>
          </p>
        </li>

        <!-- v15 -->
        <li class="grid grid-cols-[2rem,1fr] gap-x-3 p-3 leading-relaxed">
          <span
            class="col-[1] select-none text-right font-medium tabular-nums text-zinc-500"
            >15</span
          >
          <p class="col-[2]">
            I will meditate on Your precepts<br />
            And regard Your ways.
          </p>
        </li>

        <!-- v16 -->
        <li class="grid grid-cols-[2rem,1fr] gap-x-3 p-3 leading-relaxed">
          <span
            class="col-[1] select-none text-right font-medium tabular-nums text-zinc-500"
            >16</span
          >
          <p class="col-[2]">
            I shall delight in Your statutes;<br />
            I will not forget Your word.
          </p>
        </li>
      </ol>

      <!-- footnotes (optional) -->
      <aside class="mt-3 text-[0.8rem] leading-relaxed text-zinc-600">
        <p class="mb-1">
          <span class="font-medium">Notes:</span> verses from the New American Standard
          Bible (NASB)
        </p>
      </aside>
    </article>
  </div>
  <!-- <PaperPage tone="cream" grid={300} showHoles={false} className="w-screen"> -->
  <!-- <div class="max-w-2xl mx-auto min-h-60 p-4">
      <h2 class="text-xl font-semibold mb-2 special-serif">Psalm 119</h2>
      <p class="text-sm text-zinc-700 leading-relaxed special-serif">
        The poor person who lives with integrity is
        <Highlight
          color={green}
          href="https://example.com"
          mark="◦"
          ariaLabel="External link"
        >
          better
        </Highlight>.
      </p>
    </div> -->
  <div class="max-w-2xl mx-auto min-h-60 p-4 space-y-4 pb-20">
    <h2 class="text-xl font-semibold special-serif">Psalm 119</h2>

    <p class="text-sm text-zinc-700 leading-relaxed special-serif">
      The poor person who lives with integrity is
      <Highlight
        color={green}
        href="https://example.com"
        mark="◦"
        ariaLabel="External link"
      >
        better
      </Highlight>.
    </p>

    <!-- Long phrase with wrap; no link -->
    <p class="text-sm text-zinc-700 leading-relaxed special-serif">
      Wisdom begins with
      <Highlight color={yellow}>
        humble attention to the Lord’s instruction
      </Highlight>, not with self-confidence.
    </p>

    <!-- Internal cross-reference mark † -->
    <p class="text-sm text-zinc-700 leading-relaxed special-serif">
      See also
      <Highlight
        color={blue}
        href="#narratio"
        mark="†"
        ariaLabel="Internal cross-reference"
      >
        the background notes on this stanza
      </Highlight>
      for the acrostic pattern and key terms.
    </p>

    <!-- Scripture citation mark ¶; highlight only the verse numbers -->
    <p class="text-sm text-zinc-700 leading-relaxed special-serif">
      Compare
      <Highlight
        color={pink}
        href="https://www.biblegateway.com/passage/?search=Prov+3%3A5-8&version=KJV"
        mark="¶"
        ariaLabel="Scripture citation (external)"
      >
        Prov&nbsp;3:5–8
      </Highlight>
      and
      <Highlight
        color={pink}
        href="https://www.biblegateway.com/passage/?search=Ps+37%3A3-7&version=KJV"
        mark="¶"
        ariaLabel="Scripture citation (external)"
      >
        Ps&nbsp;37:3–7
      </Highlight>
      for parallel themes.
    </p>

    <!-- Emphasis inside highlight and punctuation handling -->
    <p class="text-sm text-zinc-700 leading-relaxed special-serif">
      The psalmist says,
      <Highlight color={yellow}
        ><em>“I will delight in Your statutes”</em></Highlight
      >, which frames obedience as joy, not drudgery.
    </p>

    <!-- Multi-line block to check alignment/offset -->
    <p class="text-sm text-zinc-700 leading-relaxed special-serif">
      Practically, begin with a small step:
      <Highlight color={green}>
        meditate on one command and practice it today
      </Highlight>; tomorrow, add another.
    </p>
  </div>
  <!-- </PaperPage> -->
</div>
