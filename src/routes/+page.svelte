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
    cta={{ label: "Plan Your Visit", href: "/plan-your-visit" }}
    secondary={{ label: "Learn More", href: "/about" }}
  />

  <div class="w-screen bg-sky-500 text-white relative mt-20">
    <div class="max-w-xl mx-auto min-h-60 px-6 space-y-4 py-20">
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
  </div>
</div>
