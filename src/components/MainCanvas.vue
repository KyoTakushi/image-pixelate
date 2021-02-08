<template>
  <div>
    <img id ="img1" ref="img" src="../assets/logo.png" />
    <canvas id="canvas" ref="canvas"></canvas>
  </div>
</template>

<script>
export default {
  name: 'MainCanvas',
  mounted() {
    this.pixelated = new Image()
    this.pixelated.src = this.$refs.img.src
    this.draw()
  },
  methods: {
    draw: function() {
      this.pixelated.onload = () => {
        this.imgW = this.$refs.img.clientWidth
        this.imgH = this.$refs.img.clientHeight
        this.canvas = this.$refs.canvas
        this.w = this.imgW
        this.h = this.imgH
        this.canvas.width = this.w
        this.canvas.height = this.h
        this.ctx = this.$refs.canvas.getContext('2d')
        this.ctx.msImageSmoothingEnabled = false;
        this.ctx.mozImageSmoothingEnabled = false;
        this.ctx.webkitImageSmoothingEnabled = false;
        this.ctx.imageSmoothingEnabled = false;
        
        // drawImage( image, sx, sy, sw, sh )
        // render small image
        this.ctx.drawImage(this.pixelated, 0, 0, this.w * 0.2, this.h * 0.2);

        // drawImage( image, sx, sy, sw, sh, dx, dy, dw, dh )
        // enlarge small image
        this.ctx.drawImage(this.canvas, 0, 0, this.w * 0.2, this.h * 0.2, 0, 0, this.canvas.width, this.canvas.height)
      }
    }
  },
}
</script>