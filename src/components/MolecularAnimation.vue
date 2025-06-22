<template>
  <div class="molecular-animation">
    <canvas ref="canvas" :width="canvasWidth" :height="canvasHeight"></canvas>
  </div>
</template>

<script>
export default {
  name: 'MolecularAnimation',
  data() {
    return {
      canvasWidth: 0,
      canvasHeight: 0,
      ctx: null,
      molecules: [],
      animationId: null,
      mouseX: 0,
      mouseY: 0
    }
  },
  mounted() {
    this.initCanvas()
    this.createMolecules()
    this.animate()
    this.addEventListeners()
  },
  beforeUnmount() {
    if (this.animationId) {
      cancelAnimationFrame(this.animationId)
    }
  },
  methods: {
    initCanvas() {
      this.canvasWidth = window.innerWidth
      this.canvasHeight = window.innerHeight
      this.ctx = this.$refs.canvas.getContext('2d')
    },
    createMolecules() {
      const numMolecules = 50
      for (let i = 0; i < numMolecules; i++) {
        this.molecules.push({
          x: Math.random() * this.canvasWidth,
          y: Math.random() * this.canvasHeight,
          vx: (Math.random() - 0.5) * 0.5,
          vy: (Math.random() - 0.5) * 0.5,
          radius: Math.random() * 3 + 1,
          opacity: Math.random() * 0.5 + 0.3,
          color: this.getRandomColor()
        })
      }
    },
    getRandomColor() {
      const colors = ['#14b8a6', '#0d9488', '#2dd4bf', '#5eead4']
      return colors[Math.floor(Math.random() * colors.length)]
    },
    animate() {
      this.ctx.clearRect(0, 0, this.canvasWidth, this.canvasHeight)
      
      this.molecules.forEach(molecule => {
        // Update position
        molecule.x += molecule.vx
        molecule.y += molecule.vy
        
        // Bounce off walls
        if (molecule.x < 0 || molecule.x > this.canvasWidth) molecule.vx *= -1
        if (molecule.y < 0 || molecule.y > this.canvasHeight) molecule.vy *= -1
        
        // Mouse interaction
        const dx = this.mouseX - molecule.x
        const dy = this.mouseY - molecule.y
        const distance = Math.sqrt(dx * dx + dy * dy)
        
        if (distance < 100) {
          const force = (100 - distance) / 100
          molecule.vx += dx * force * 0.001
          molecule.vy += dy * force * 0.001
        }
        
        // Draw molecule
        this.ctx.beginPath()
        this.ctx.arc(molecule.x, molecule.y, molecule.radius, 0, Math.PI * 2)
        this.ctx.fillStyle = molecule.color + Math.floor(molecule.opacity * 255).toString(16).padStart(2, '0')
        this.ctx.fill()
      })
      
      // Draw connections
      this.drawConnections()
      
      this.animationId = requestAnimationFrame(this.animate)
    },
    drawConnections() {
      this.molecules.forEach((molecule, i) => {
        this.molecules.slice(i + 1).forEach(other => {
          const dx = molecule.x - other.x
          const dy = molecule.y - other.y
          const distance = Math.sqrt(dx * dx + dy * dy)
          
          if (distance < 80) {
            const opacity = (80 - distance) / 80 * 0.3
            this.ctx.beginPath()
            this.ctx.moveTo(molecule.x, molecule.y)
            this.ctx.lineTo(other.x, other.y)
            this.ctx.strokeStyle = `rgba(20, 184, 166, ${opacity})`
            this.ctx.lineWidth = 1
            this.ctx.stroke()
          }
        })
      })
    },
    addEventListeners() {
      window.addEventListener('mousemove', (e) => {
        this.mouseX = e.clientX
        this.mouseY = e.clientY
      })
      
      window.addEventListener('resize', () => {
        this.canvasWidth = window.innerWidth
        this.canvasHeight = window.innerHeight
      })
    }
  }
}
</script>

<style scoped>
.molecular-animation {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: -1;
}

canvas {
  display: block;
}
</style>