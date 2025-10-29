<script lang="ts">
  // Props
  export let href: string | undefined = undefined; // when present, renders <a>
  export let color: string = "oklch(0.93 0.07 100)"; // highlight fill
  export let thicknessEm = 0.9; // highlight thickness (em)
  export let yPercent = 85; // vertical position of the stroke (0–100)
  export let noisy = true; // irregular edges
  export let mark: string | null = null; // e.g., '◦', '†', '¶' (optional)
  export let ariaLabel: string | undefined; // optional aria label for links
  export let rel: string | undefined; // e.g., 'noopener noreferrer'
  export let target: string | undefined; // e.g., '_blank'

  // Inline SVG noise mask (cheap; adjustable seed if you want variants)
  const noiseUrl =
    'url("data:image/svg+xml;utf8,' +
    "<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 80 20' preserveAspectRatio='none'>" +
    "<filter id='n'><feTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='2' seed='7'/>" +
    "<feColorMatrix type='saturate' values='0'/></filter>" +
    "<rect width='100%' height='100%' fill='white' filter='url(%23n)'/></svg>\")";
</script>

<!-- <svelte:element
  this={href ? "a" : "span"}
  {...href ? { href, rel, target, "aria-label": ariaLabel } : {}}
  class={`hl ${href ? "is-link" : ""} ${noisy ? "is-noisy" : ""} `}
  style={`--hl:${color}; --thick:${thicknessEm}em; --y:${yPercent}%; --noise:${noiseUrl};`}
>
  <slot />
  {#if mark}
    <sup class="mark" aria-hidden="true">{mark}</sup>
    {#if ariaLabel}<span class="sr-only"> ({ariaLabel})</span>{/if}
  {/if}
</svelte:element> -->
<svelte:element
  this={href ? "a" : "span"}
  {...href ? { href, rel, target, "aria-label": ariaLabel } : {}}
  class="hl"
  style={`
    --hl-color:${color};
    --hl-height:${thicknessEm}em;
    --hl-offset:${yPercent}%;
    --hl-pad-start:0.10em;
    --hl-pad-end:0.02em;
  `}
>
  <slot />
  {#if mark}<sup class="mark" aria-hidden="true">{mark}</sup>{/if}
  {#if href && ariaLabel}<span class="sr-only"> ({ariaLabel})</span>{/if}
</svelte:element>

<style>
  /* hand-drawn highlighter with skewed ends + soft vertical fade */
  .hl {
    /* expects CSS vars set inline (see above) */
    color: inherit;
    text-decoration: none;
    position: relative;

    padding-inline-start: var(--hl-pad-start);
    padding-inline-end: var(--hl-pad-end);

    /* 1) left cap  2) middle bar with vertical fade  3) right cap */
    background-image: linear-gradient(
        to bottom right,
        transparent 48%,
        var(--hl-color) 50%
      ),
      linear-gradient(
        to bottom,
        transparent 6%,
        color-mix(in oklab, var(--hl-color), transparent 20%) 18%,
        var(--hl-color) 50%,
        color-mix(in oklab, var(--hl-color), transparent 20%) 82%,
        transparent 94%
      ),
      linear-gradient(to top left, transparent 48%, var(--hl-color) 50%);
    background-size:
      var(--hl-skew, 0.28em) var(--hl-height),
      calc(100% - (var(--hl-skew, 0.28em) * 2)) var(--hl-height),
      var(--hl-skew, 0.28em) var(--hl-height);
    background-position:
      left calc(100% - var(--hl-offset)),
      center calc(100% - var(--hl-offset)),
      right calc(100% - var(--hl-offset));
    background-repeat: no-repeat;

    /* subtle pressure line */
    box-shadow: inset 0 calc(-1 * var(--hl-height) / 18) 0 rgb(0 0 0 / 0.12);
  }

  /* non-color affordance for links */
  a.hl:hover,
  a.hl:focus {
    border-bottom: 0.06em dotted currentColor;
    outline: none;
  }
  a.hl:focus-visible {
    outline: 2px solid currentColor;
    outline-offset: 2px;
  }

  .mark {
    font-size: 0.7em;
    vertical-align: super;
    margin-left: 0.15em;
  }
  .sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 1px, 1px);
    white-space: nowrap;
    border: 0;
  }
</style>
