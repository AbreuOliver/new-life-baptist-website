<script lang="ts">
  export let radius: number;
  export let animClass = "animate-[spin_4s_linear_infinite]"; // applied to ARC group only
  export let className = "absolute inset-0 h-full w-full";

  // geometry + base ring
  export let strokeWidth = 1.125;
  export let baseStroke = "#D4D4D4";
  export let baseOpacity = 0.7;

  // colors (CSS var name like "--color-…" or literal like "#05BBF8")
  export let fromColor: string = "--color-brand-500";
  export let toColor: string = "--color-cta-from";

  // tail fade behavior
  export let tail = 0.65; // where the gradient reaches full fade (0..1 along the arc)
  export let headHold = 0.1; // keep head fully opaque for this fraction (0..1)
  // export let tailMinOpacity = 0.25; // minimum opacity at end of tail (0..1), >0 makes tail more visible

  // head appearance
  export let headWidthMul = 1.8; // head stroke is mul * strokeWidth (e.g. 1.8x thicker)
  export let headLen = 0.12; // fraction of arc length shown as the “head” (0..1)

  const cx = 513,
    cy = 513;
  $: R = radius;
  $: xRight = cx + R;
  $: yBottom = cy + R;

  // Quarter arc: right -> bottom
  $: arcD = `M ${xRight} ${cy} A ${R} ${R} 0 0 1 ${cx} ${yBottom}`;

  // detect reverse from animClass
  $: isReverse = /\breverse\b/.test(animClass);

  function resolve(c: string) {
    return c?.trim().startsWith("--") ? `var(${c})` : c;
  }
  $: from = resolve(fromColor);
  $: to = resolve(toColor);

  // clamp
  $: t = Math.max(0, Math.min(1, tail));
  $: h = Math.max(0, Math.min(1, headHold));
  $: headFrac = Math.max(0, Math.min(1, headLen));

  // ids
  const uid = Math.random().toString(36).slice(2);
  $: gradId = `grad-${uid}`;

  export let headGap = 0.06; // portion at the very end kept transparent under the head
  export let tailPeak = 0.5; // max opacity the tail reaches (0..1)

  $: g = Math.max(0, Math.min(0.3, headGap)); // clamp a sane gap
  $: p = Math.max(0, Math.min(1, tailPeak)); // clamp peak opacity

  // place after your existing props
  // len = fraction of arc length for that step; mul = width multiplier; op = opacity
  // export let headSteps: { len: number; mul: number; op?: number }[] = [
  //   { len: 0.12, mul: 1.9, op: 1.0 },
  //   { len: 0.09, mul: 1.55, op: 0.9 },
  //   { len: 0.06, mul: 1.3, op: 0.8 },
  //   { len: 0.04, mul: 1.15, op: 0.7 },
  // ];

  export let headSteps = [
    { len: 0.12, mul: 1.9, op: 1.0 },
    { len: 0.08, mul: 1.55, op: 0.9 },
    { len: 0.05, mul: 1.3, op: 0.8 },
    { len: 0.03, mul: 1.15, op: 0.7 },
    { len: 0.02, mul: 1.05, op: 0.6 }, // last step gets cap="butt"
  ];

  // reuse your existing isReverse and head positioning logic:
  $: headDashOffsetBase = isReverse ? 0 : 1; // start (0) for reverse, end (1) for normal
</script>

<svg viewBox="0 0 1026 1026" fill="none" aria-hidden="true" class={className}>
  <!-- static full ring -->
  <circle
    {cx}
    {cy}
    r={R}
    stroke={baseStroke}
    stroke-opacity={baseOpacity}
    stroke-width={strokeWidth}
    vector-effect="non-scaling-stroke"
    fill="none"
  />

  <!-- rotating group: tail layer + multi-step tapered head -->
  <g
    class={`${animClass} [transform-box:view-box] [transform-origin:513px_513px]`}
  >
    <!-- tail layer (full quarter arc, faded) -->
    <path
      d={arcD}
      stroke={`url(#${gradId})`}
      stroke-linecap="round"
      stroke-width={strokeWidth}
      vector-effect="non-scaling-stroke"
      fill="none"
    />

    <!-- tapered head: several shorter/thinner segments -->
    <!-- replace the head layer loop with cap control -->
    {#each headSteps as step, i}
      {@const len = Math.max(0, Math.min(1, step.len))}
      {@const mul = Math.max(0, step.mul)}
      {@const op = step.op ?? 1}
      {@const cap = i === headSteps.length - 1 ? "butt" : "round"}

      <path
        d={arcD}
        pathLength="1"
        stroke={from}
        stroke-opacity={op}
        stroke-linecap={cap}
        stroke-width={strokeWidth * mul}
        stroke-dasharray={`${len} 1`}
        stroke-dashoffset={isReverse ? 0 : 1 - len}
        vector-effect="non-scaling-stroke"
        fill="none"
      />
    {/each}
  </g>

  <defs>
    <linearGradient
      id={gradId}
      gradientUnits="objectBoundingBox"
      x1="1"
      y1="0.5"
      x2="0.5"
      y2="1"
    >
      {#if isReverse}
        <!-- CCW: start is the head; keep a gap right at start -->
        <stop offset="0" stop-color={from} stop-opacity="0" />
        <stop offset={g} stop-color={from} stop-opacity="0" />
        <stop offset={Math.max(g, h)} stop-color={from} stop-opacity={p} />
        <stop offset={t} stop-color={to} stop-opacity={p} />
        <stop offset="1" stop-color={to} stop-opacity={p} />
      {:else}
        <!-- CW: end is the head; keep a gap right before the end -->
        <stop offset="0" stop-color={to} stop-opacity={p} />
        <stop offset={t} stop-color={to} stop-opacity={p} />
        <stop offset={Math.max(t, 1 - g)} stop-color={from} stop-opacity={0} />
        <stop offset="1" stop-color={from} stop-opacity={0} />
      {/if}
    </linearGradient>
  </defs>
</svg>
