

Vue.component("swatch", {
	props: ["active", "swatch", "effect"],
	template: `
		<div class="grid-item">
			<div class="grid-cell--top" :style="effect(swatch)" >
				
			</div>
			<div class="grid-cell--bottom" :style="corrected_color()">
				{{ swatch.color.toUpperCase() }}
			</div>
		</div>
	`, 
    methods: {
        corrected_color: function () {
            return {
                color: this.swatch.color == '#ffffff' ? '#000000' : this.swatch.color
            }
        }
    }
})

var app = new Vue({
	el: "#app",
	data: {
		active: "",
		swatches: [
		    { color: "#ff691f" },
		    { color: "#fab81e" },
		    { color: "#7fdbb6" },
		    { color: "#19cf86" },
		    { color: "#91d2fa" },
		    { color: "#1b95e0" },
		    { color: "#abb8c2" },
		    { color: "#e81c4f" },
		    { color: "#f58ea8" },
		    { color: "#981ceb" },
		    { color: "#ffffff" },
		    { color: "#000000" },
		],
	},
	methods: {
		activate: function (swatch) {
			this.active = swatch
		},
		gradient: function (swatch) {
			return {
				background: "linear-gradient(100deg, whitesmoke -100%, " + swatch.color + ")",
			}
		}
	}
})