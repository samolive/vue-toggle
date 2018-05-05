<template>
    <div class="toggle-component" @click="$emit('toggled')" :style="styleParent">
        <p class="-label" :style="styleLeft">{{leftText}}</p>
        <p class="-label" :style="styleRight">{{rightText}}</p>
    </div>
</template>

<script>
	export default {
		name: "Toggle",
        props: {
	        value:Boolean,
	        leftText:{default: 'Sim',},
	        rightText:{default: 'Não',},
	        textSize:{default: '0.7rem',},
	        toggleHeight:{default: '2.1rem',},
            widthFactor:{default: 0.5,},
	        borderColor:{default: '#535353',},
	        leftTrueColor:{default: '#ffffff',},
	        leftFalseColor:{default: '#535353',},
	        leftTrueBgcolor:{default: '#41b883',},
	        leftFalseBgcolor:{default: '#ffffff',},
	        rightTrueColor:{default: '#535353',},
	        rightFalseColor:{default: '#ffffff',},
	        rightTrueBgcolor:{default: '#ffffff',},
	        rightFalseBgcolor:{default: '#ff3860',},
        },
        	
        data(){
	        return {
	        	styleParent:{
			        border: `solid 1px ${this.borderColor}`,
			        fontSize: this.textSize,
			        height: this.toggleHeight,
			        lineHeight: this.toggleHeight,
			        minWidth: '6rem',
			        maxWidth: '6rem',
                },
	        	styleLeft:{
	        		color: this.leftTrueColor,
			        backgroundColor: this.leftTrueBgcolor,
			        minWidth: '5rem',
			        maxWidth: '5rem',
			        marginLeft: '0',
                },
	        	styleRight:{
	        		color: this.rightTrueColor,
			        backgroundColor: this.rightTrueBgcolor,
			        minWidth: '5rem',
			        maxWidth: '5rem',
                },
	        }
        },
        created(){
	        this.styleParent = {
		        border: `solid 1px ${this.borderColor}`,
			        fontSize: this.textSize,
			        height: this.toggleHeight,
			        lineHeight: this.toggleHeight,
			        minWidth: `${this.width+2}rem`,
			        maxWidth: `${this.width+2}rem`,
	        };
	        this.styleLeft = {
		        color: this.value ? this.leftTrueColor : this.leftFalseColor,
			        backgroundColor: this.value ? this.leftTrueBgcolor : this.leftFalseBgcolor,
			        minWidth: `${this.width+1}rem`,
			        maxWidth: `${this.width+1}rem`,
			        marginLeft: this.value ? '0' : `-${this.width}rem`,
	        };
	        this.styleRight= {
		        color: this.value ? this.rightTrueColor : this.rightFalseColor,
			        backgroundColor: this.value ? this.rightTrueBgcolor : this.rightFalseBgcolor,
		        minWidth: `${this.width+1}rem`,
		        maxWidth: `${this.width+1}rem`,
	        };
        },
        watch: {
			value: function(val,old){
				this.styleLeft = {
					color: this.value ? this.leftTrueColor : this.leftFalseColor,
					backgroundColor: this.value ? this.leftTrueBgcolor : this.leftFalseBgcolor,
					minWidth: `${this.width+1}rem`,
					maxWidth: `${this.width+1}rem`,
					marginLeft: this.value ? '0' : `-${this.width}rem`,
				};
				this.styleRight= {
					color: this.value ? this.rightTrueColor : this.rightFalseColor,
					backgroundColor: this.value ? this.rightTrueBgcolor : this.rightFalseBgcolor,
					minWidth: `${this.width+1}rem`,
					maxWidth: `${this.width+1}rem`,
				};

            }
        },
        computed: {
			width() {
				return Math.max(this.leftText.length, this.rightText.length)*this.widthFactor
            }
        }
	}
</script>

<style scoped lang="scss">
    .toggle-component{
        position: relative;
        transition: all 0.4s ease-in-out;
        display: flex;
        text-transform: uppercase;
        text-align: center;
        cursor:pointer;
        overflow: hidden;
        >.-label{
            transition: all 0.4s ease-in-out;
            text-align: center;
        }

    }
</style>