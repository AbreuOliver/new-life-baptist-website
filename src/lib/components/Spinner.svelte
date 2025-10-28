<script lang="ts">
  export let radius: number;
  export let animClass = "";
  export let baseStroke = "#D4D4D4";
  export let baseOpacity = 0.7;
  export let fromColor: string = "#000";
  export let toColor: string = "#333";

  // NEW: one shared coordinate system and an auto-scaler
  export let viewBoxSize = 2200; // big enough for your largest ring
  export let designBase = 1026; // what your radii were authored for

  const resolve = (c: string) => (c.trim().startsWith("--") ? `var(${c})` : c);
  $: from = resolve(fromColor);
  $: to = resolve(toColor);

  $: cx = viewBoxSize / 2;
  $: cy = viewBoxSize / 2;

  // scale radius from the design base to this viewBox
  $: scale = viewBoxSize / designBase;
  $: R = radius * scale;

  $: arcD = `M ${cx + R} ${cy} A ${R} ${R} 0 0 1 ${cx} ${cy + R}`;
  $: isReverse = /\breverse\b/.test(animClass);

  const uid = Math.random().toString(36).slice(2);
  $: gradId = `ring-grad-${uid}`;
</script>

<svg
  viewBox={`0 0 ${viewBoxSize} ${viewBoxSize}`}
  fill="none"
  aria-hidden="true"
  style="z-index: -1;"
  class={`absolute inset-0 h-full w-full ${animClass}`}
>
  <circle
    {cx}
    {cy}
    r={R}
    stroke={baseStroke}
    stroke-opacity={baseOpacity}
    fill="none"
    vector-effect="non-scaling-stroke"
  />
  <path
    d={arcD}
    stroke={`url(#${gradId})`}
    stroke-linecap="round"
    fill="none"
  />
  <defs>
    <linearGradient
      id={gradId}
      x1={cx + R}
      y1={cy}
      x2={cx + R}
      y2={cy + R}
      gradientUnits="userSpaceOnUse"
    >
      {#if isReverse}
        <stop offset="0" stop-color={from} />
        <stop offset="1" stop-color={to} stop-opacity="0" />
      {:else}
        <stop offset="0" stop-color={to} stop-opacity="0" />
        <stop offset="1" stop-color={from} />
      {/if}
    </linearGradient>
  </defs>
</svg>
