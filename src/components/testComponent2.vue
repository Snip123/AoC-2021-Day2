<template>
  <div class="counter">
    <textarea v-model="message" placeholder="add multiple lines"></textarea>
    <br />
    <button @click="updateData">Update</button>
    <br/>
    <span>Output:</span>
    <p style="white-space: pre-line;">{{ output }}</p>
    
  </div>
</template>

<script>

export default {
  name: 'testComponent2',
  data: function() {
    return {
      message: "",
      output: ""
    }
  },
  methods:
  {
    updateData: function () {
      
      var inputs = this.message.split('\n')
      /*inputs = ["forward 5",
"down 5",
"forward 8",
"up 3",
"down 8",
"forward 2"]*/
      var horizontal = 0;
      var depth = 0;
      var aim = 0;
      for (let index = 0; index < inputs.length; index++) {
        const components = inputs[index].split(' ');
        var direction = components[0]
        var amount = components[1]
        switch(direction)
        {
          case "forward":
            horizontal += parseInt( amount)
            depth += aim*parseInt( amount)
//this.output += "forward total " + (depth * horizontal) + " depth: " + depth + " horizontal: " + horizontal + " aim: " + aim + "\n";
            break;
          case "up":
            //depth -= parseInt( amount)
            aim -= parseInt( amount)
//this.output += "up total " + (depth * horizontal) + " depth: " + depth + " horizontal: " + horizontal + " aim: " + aim + "\n";
            break;
          case "down":
            //depth += parseInt( amount)
            aim += parseInt( amount)
//this.output += "down total " + (depth * horizontal) + " depth: " + depth + " horizontal: " + horizontal + " aim: " + aim + "\n";
            break;
          default:
        }
      }
this.output += "total " + (depth * horizontal) + " depth: " + depth + " horizontal: " + horizontal + " aim: " + aim + "\n";
      
    }
  },
}
</script>

