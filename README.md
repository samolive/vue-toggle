# vue-toggle
Vue.js UI toggle component

##Usage

###Required Props
- value (boolean)

##Emitted event
- 'toggled'

###Example

`<toggle :value="active" 
@toggled="actionMethod()" 
:toggleHeight="'1.5rem'" 
:widthFactor="0.5" 
:borderColor="'#dedede'"
:leftText="'Active'"
:rightText="'Inactive'"
/>


