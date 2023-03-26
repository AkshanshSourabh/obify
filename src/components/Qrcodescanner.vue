<!-- <template>
<div class="flex h-screen">
    <div class="w-1/2 h-96  m-auto">
        <qrcode-stream @decode="onDecode" :track="drawOutline"></qrcode-stream>
    </div>
</div>
</template>

<script>
import {
    QrcodeStream
} from 'vue-qrcode-reader'

export default {
    components: {
        QrcodeStream
    },
    methods: {
        onDecode(decodeString) {
            console.log(decodeString)
        },

        drawOutline(decodeData, context) {

            // let points = [];
            var points = Array(4).fill({});

            // var points = [];
            for (var k in decodeData) {
                switch (k) {
                    case "topLeftCorner":
                        console.log(k)
                        points[0] = decodeData[k];
                        break;
                    case "topRightCorner":
                        points[1] = decodeData[k];
                        break;
                    case "bottomRightCorner":
                        points[2] = decodeData[k];
                        break;
                    case "bottomLeftCorner":
                        points[3] = decodeData[k];
                        break;
                    default:
                        break;
                }
            }
            for (let i = 0; i < points.length; i++) {
                context.fillStyle = "green";
                context.beginPath();
                context.arc(points[i].x, points[i].y, 10, 0, 2 * Math.PI);
                context.fill();
            }

            context.lineWidth = 30
            context.strokeStyle = 'red'
            context.beginPath()
            console.log(points[0])
            context.moveTo(points[0].x, points[0].y)

            for (const {
                    x,
                    y
                } of points) {
                context.lineTo(x, y)
            }
            context.lineTo(points[0].x, points[0].y)
            context.closePath()
            context.stroke()

        },

    },

};
</script>

<style lang="scss" scoped>

</style> -->
<!-- <template>
    <div class="flex h-screen">
      <div class="w-1/2 h-96  m-auto">
        <qrcode-stream @decode="onDecode" :track="drawOutline"></qrcode-stream>
      </div>
    </div>
  </template>
  
  <script>
  import { QrcodeStream } from 'vue-qrcode-reader'
  
  export default {
    components: {
      QrcodeStream
    },
    methods: {
      onDecode(decodeString) {
        console.log(decodeString)
      },
  
      drawOutline(decodeData, context) {
        var points = Array(4).fill({});
        for (var k in decodeData) {
          switch (k) {
            case "topLeftCorner":
              console.log(k)
              points[0] = decodeData[k];
              break;
            case "topRightCorner":
              points[1] = decodeData[k];
              break;
            case "bottomRightCorner":
              points[2] = decodeData[k];
              break;
            case "bottomLeftCorner":
              points[3] = decodeData[k];
              break;
            default:
              break;
          }
        }
  
        // Draw green circles around the QR code
        for (let i = 0; i < points.length; i++) {
          context.fillStyle = "green";
          context.beginPath();
          context.arc(points[i].x, points[i].y, 10, 0, 2 * Math.PI);
          context.fill();
        }
  
        // Draw red border around the QR code
        context.lineWidth = 30;
        context.strokeStyle = "red";
        context.beginPath();
        context.moveTo(points[0].x, points[0].y);
        for (const { x, y } of points) {
          context.lineTo(x, y);
        }
        context.lineTo(points[0].x, points[0].y);
        context.closePath();
        context.stroke();
      },
    },
  };
  </script>
  
  <style lang="scss" scoped>
  </style> -->
  <template>
    <div class="flex h-screen">
      <div class="w-1/2 h-96 m-auto relative">
        <div class="absolute inset-0 bg-black opacity-50 z-10"></div> <!-- Faded camera screen -->
        <div class="absolute inset-0 flex items-center justify-center z-20">
          <div class="w-64 h-64 relative">
            <div class="absolute inset-0 border-4 border-white"></div> <!-- Square cutout for QR code -->
            <qrcode-stream @decode="onDecode" :track="drawOutline"></qrcode-stream>
            <canvas ref="canvas" class="absolute inset-0"></canvas>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import { QrcodeStream } from 'vue-qrcode-reader'
  import canvas from 'canvas';

  export default {
    components: {
      QrcodeStream
    },
    methods: {
      onDecode(decodeString) {
        console.log(decodeString)
      },
  
      drawOutline(decodeData, context) {
        var points = Array(4).fill({});
        for (var k in decodeData) {
          switch (k) {
            case "topLeftCorner":
              console.log(k)
              points[0] = decodeData[k];
              break;
            case "topRightCorner":
              points[1] = decodeData[k];
              break;
            case "bottomRightCorner":
              points[2] = decodeData[k];
              break;
            case "bottomLeftCorner":
              points[3] = decodeData[k];
              break;
            default:
              break;
          }
        }
  
        // Draw green circles around the QR code
        for (let i = 0; i < points.length; i++) {
          context.fillStyle = "green";
          context.beginPath();
          context.arc(points[i].x, points[i].y, 10, 0, 2 * Math.PI);
          context.fill();
        }
  
        // Draw red border around the QR code
        context.lineWidth = 30;
        context.strokeStyle = "red";
        context.beginPath();
        context.moveTo(points[0].x, points[0].y);
        for (const { x, y } of points) {
          context.lineTo(x, y);
        }
        context.lineTo(points[0].x, points[0].y);
        context.closePath();
        context.stroke();
      },
    },
    mounted() {
      this.canvas = this.$refs.canvas;
      this.context = this.canvas.getContext("2d");
    },
  };
  </script>
  
  <style lang="scss" scoped>
  /* Style for the square cutout */
  canvas {
    mix-blend-mode: screen; /* This blends the canvas with the background to create a faded effect */
  }
  canvas ~ div {
    pointer-events: none;
  }
  </style>