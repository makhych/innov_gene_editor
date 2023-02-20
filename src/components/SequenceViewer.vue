<template>
    <div>
      <canvas ref="canvas"></canvas>
    </div>
</template>
  
<script>
  export default {
    name: "SequenceViewer",
    props: {
      sequence: {
        type: String,
        required: true
      }
    },
    mounted() {
      this.drawSequence();
    },
    methods: {
      drawSequence() {
        const canvas = this.$refs.canvas;
        const context = canvas.getContext("2d");
        const sequence = this.sequence.toUpperCase();
        const sequenceLength = sequence.length;
        const canvasWidth = canvas.width;
        const canvasHeight = canvas.height;
        const nucleotideColors = {
          A: "#009900",
          C: "#0000FF",
          G: "#FF6600",
          T: "#CC0000"
        };
        const nucleotideWidth = canvasWidth / sequenceLength;
        for (let i = 0; i < sequenceLength; i++) {
          const nucleotide = sequence.charAt(i);
          const nucleotideColor = nucleotideColors[nucleotide] || "#FFFFFF";
          context.fillStyle = nucleotideColor;
          context.fillRect(i * nucleotideWidth, 0, nucleotideWidth, canvasHeight);
        }
      }
    }
  };
</script>