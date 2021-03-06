<template lang="pug">
div
  w-card(bg-color="blue-light5")
    p First choose your progress style:
    w-radios.title3(v-model="circular" :items="linearOrCircular" inline)

  //- Circular progress.
  //-------------------------------------------------------
  div(v-if="circular")
    title-link(h2) Default indeterminate progress &amp; colors
    p.
      Like in most components, you can set a #[code color] for the text and a #[code bg-color] for the
      background.#[br]
      By default, the progress foreground color is #[code primary].
    example(reactive)
      w-progress.ma1(circle)
      w-progress.ma1(circle color="blue")
      w-progress.ma1(circle color="green")

      h3 Mixing colors

      w-progress.ma1(circle color="yellow" bg-color="cyan")
      template(#pug).
        w-progress.ma1(circle)
        w-progress.ma1(circle color="blue")
        w-progress.ma1(circle color="green")

        .title3.my6 Mixing colors
        w-progress.ma1(circle color="yellow" bg-color="cyan")

    title-link(h2) Progress value
    p The value can be given as a number or a string.
    p.
      When the value is #[code undefined], #[code -1] or not provided at all, it will be assumed
      indeterminate.
    example(reactive)
      w-progress.ma1(circle :value="undefined")
      w-progress.ma1.mr8(circle :value="-1")
      w-progress.ma1(circle value="0")
      w-progress.ma1(circle value="12.5")
      w-progress.ma1(circle value="25")
      w-progress.ma1(circle value="50")
      w-progress.ma1(circle value="75")
      w-progress.ma1(circle value="100")
      template(#pug).
        w-progress.ma1(circle :value="undefined")
        w-progress.ma1.mr8(circle :value="-1")

        w-progress.ma1(circle value="0")
        w-progress.ma1(circle value="12.5")
        w-progress.ma1(circle value="25")
        w-progress.ma1(circle value="50")
        w-progress.ma1(circle value="75")
        w-progress.ma1(circle value="100")

    h3 Updated value example
    example(reactive)
      w-progress(circle :value="progress")
      template(#pug).
        w-progress(circle :value="progress")
      template(#js).
        data: () => ({
          progress: 0
        }),

        mounted () {
          // Emulating progress.
          setInterval(() => {
            this.progress += 10
            if (this.progress === 100) this.progress = 0
          }, 700)
        }

    title-link(h2) Size &amp; stroke thickness
    example(reactive)
      w-progress.ma1(circle value="38" color="blue")
      w-progress.ma1(circle value="38" size="4em" color="blue")
      w-progress.ma1.mr8(circle value="38" size="5em" color="blue")
      w-progress.ma1(circle value="38" size="6em" :stroke="2" color="blue")
      w-progress.ma1(circle value="38" size="6em" :stroke="15" color="blue")
      w-progress.ma1(circle value="38" size="6em" :stroke="40" color="blue")
      template(#pug).
        w-progress.ma1(circle value="38" color="blue")
        w-progress.ma1(circle value="38" size="4em" color="blue")
        w-progress.ma1.mr8(circle value="38" size="5em" color="blue")

        w-progress.ma1(circle value="38" size="6em" :stroke="2" color="blue")
        w-progress.ma1(circle value="38" size="6em" :stroke="15" color="blue")
        w-progress.ma1(circle value="38" size="6em" :stroke="40" color="blue")

    title-link(h2) Progress value with label
    p The default label displays the rounded value without the #[code %] sign, so it fits in smaller circles.
    p You can customize the label to display the value as you wish.
    example(reactive)
      p Default label &nbsp; - &nbsp; Custom label
      w-progress.ma1.mr8(circle v-model="progress1" size="5em" label)
      w-progress.ma1(circle v-model="progress1" size="5em")
        strong {{ progress1 }}%
      template(#pug).
        p Default label - Custom label

        w-progress.ma1.mr8(circle v-model="progress" size="5em" label)

        w-progress.ma1(circle v-model="progress" size="5em")
          strong {{ '\{\{ progress \}\}' }}%
      template(#js).
        data: () => ({
          progress: 37.86
        })

    h3 Providing a color for the custom label
    example(reactive)
      w-progress.ma1(
        circle
        value="38"
        size="3em"
        label
        label-color="indigo-light4")
      template(#pug).
        w-progress.ma1(
          circle
          value="38"
          size="3em"
          label
          label-color="indigo-light4")

    title-link(h2) Round linecap &amp; default flat line cap
    example(reactive)
      w-progress.ma1(circle value="38" size="6em" round-cap)
      w-progress.ma1(circle value="38" size="6em")
      template(#pug).
        w-progress.ma1(circle value="38" size="6em" round-cap)
        w-progress.ma1(circle value="38" size="6em")

  //- Linear progress.
  //-------------------------------------------------------
  div(v-else)
    title-link(h2) Default indeterminate progress &amp; colors
    p.
      Like in most components, you can set a #[code color] for the text and a #[code bg-color] for the
      background.
    example(reactive)
      w-progress
      w-progress.mt4(color="blue")
      w-progress.mt4(color="green")
      h3 Mixing colors
      w-progress.mt4(color="yellow" bg-color="cyan")
      template(#pug).
        w-progress
        w-progress.mt4(color="blue")
        w-progress.mt4(color="green")
        .title3.my6 Mixing colors
        w-progress.mt4(color="yellow" bg-color="cyan")

    title-link(h2) Size
    example(reactive)
      w-progress(value="38" size="1em" color="blue")
      w-progress.mt4(value="38" size="2.5em" color="blue")
      template(#pug).
        w-progress(value="38" size="1em" color="blue")
        w-progress.mt4(value="38" size="2.5em" color="blue")

    title-link(h2) Tile &amp; round
    example(reactive)
      w-progress(value="38" size="1.4em" tile color="light-blue")
      w-progress.mt4(value="38" size="1.4em" round color="light-blue")
      template(#pug).
        w-progress(value="38" size="1.4em" tile color="light-blue")
        w-progress.mt4(value="38" size="1.4em" round color="light-blue")

    title-link(h2) Outline &amp; shadow
    example(reactive)
      w-progress(value="38" size="1em" outline round color="light-blue")
      w-progress.mt4(value="38" size="1em" shadow color="light-blue")
      template(#pug).
        w-progress(value="38" size="1em" outline round color="light-blue")
        w-progress.mt4(value="38" size="1em" shadow color="light-blue")

    title-link(h2) Stripes (only if determinate)
    example(reactive)
      w-progress(
        value="38"
        size="1em"
        outline
        round
        color="light-blue"
        stripes)
      w-progress.mt4(
        value="38"
        size="1.4em"
        outline
        round
        color="primary"
        stripes)
      template(#pug).
        w-progress(
          value="38"
          size="1em"
          outline
          round
          color="light-blue"
          stripes)
        w-progress.mt4(
          value="38"
          size="1.4em"
          outline
          round
          color="primary"
          stripes)

    title-link(h2) Progress value with label
    h3 Default label
    example(reactive)
      w-progress(v-model="progress1" size="1.3em" round color="primary" label)
      w-progress.mt4(v-model="progress1" size="1.3em" outline round label)
      template(#pug).
        w-progress(v-model="progress" size="1.3em" round color="primary" label)
        w-progress.mt4(v-model="progress" size="1.3em" outline round label)
      template(#js).
        data: () => ({
          progress: 37.86
        })

    h3 Custom label
    example(reactive)
      w-progress.mt3(v-model="progress1" size="1.5em" outline round)
        strong {{ progress1 }}%
      template(#pug).
        w-progress(v-model="progress" size="1.5em" outline round)
          strong {{ '\{\{ progress \}\}' }}%
      template(#js).
        data: () => ({
          progress: 37.86
        })

    h3 Providing a color for the custom label
    p.
      The color of the label should be readable on both the progress and the background.#[br]
      So you are free to decide what is the best color.
    example(reactive)
      w-progress.mt2(
        value="50.3"
        size="2em"
        outline
        round
        label
        label-color="indigo-light4")
      template(#pug).
        w-progress(
          value="50.3"
          size="2em"
          outline
          round
          label
          label-color="indigo-light4")

    title-link(h2) Round linecap &amp; default flat line cap
    example(reactive)
      w-progress(value="38" size="2em" round round-cap)
      w-progress.mt4(value="38" size="2em" round)
      template(#pug).
        w-progress(value="38" size="2em" round round-cap)
        w-progress.mt4(value="38" size="2em" round)
</template>

<script>
export default {
  data: () => ({
    progress1: 37.86,
    progress: 0,
    linearOrCircular: [
      { label: 'Linear', value: false },
      { label: 'Circular', value: true }
    ],
    circular: true,
    intervalId: null
  }),

  mounted () {
    // Emulating progress.
    this.intervalId = setInterval(() => {
      this.progress += 10
      if (this.progress === 100) this.progress = 0
    }, 700)
  },

  beforeDestroy () {
    clearInterval(this.intervalId)
  }
}
</script>
