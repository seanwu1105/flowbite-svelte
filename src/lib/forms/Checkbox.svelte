<script lang="ts">
  import { getContext } from 'svelte';
  import type { FormColorType } from '../types';
  import Radio, { labelClass, inputClass } from './Radio.svelte';
  import Label from './Label.svelte';

  // properties forwarding
  export let color: FormColorType = 'blue';
  export let custom: boolean = false;
  export let inline: boolean = false;

  export let group: string[] = [];
  export let value: string = '';
  export let checked: boolean = false;

  // tinted if put in component having its own background
  let background: boolean = getContext('background');

  $: {
    // There's a bug in Svelte and bind:group is not working with wrapped checkbox
    // This workaround is taken from:
    // https://svelte.dev/repl/de117399559f4e7e9e14e2fc9ab243cc?version=3.12.1
    const index = group.indexOf(value);

    if (checked === undefined) checked = index >= 0;

    if (checked) {
      if (index < 0) {
        group.push(value);
        group = group;
      }
    } else {
      if (index >= 0) {
        group.splice(index, 1);
        group = group;
      }
    }
  }
</script>

<Label class={labelClass(inline, $$props.class)} show={!!$$slots.default}>
  <input
    type="checkbox"
    bind:checked
    on:keyup
    on:keydown
    on:keypress
    on:focus
    on:blur
    on:click
    on:mouseover
    on:mouseenter
    on:mouseleave
    on:paste
    {value}
    {...$$restProps}
    class={inputClass(custom, color, true, background, $$slots.default || $$props.class)} /><slot />
</Label>
