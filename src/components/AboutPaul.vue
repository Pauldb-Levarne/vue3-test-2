<script setup lang="ts">
import { computed, onMounted, reactive, ref, watch } from "vue";

interface personObject {
	name?: string;
	github?: string;
	linkedIn?: string;
}

const paulsInfo: personObject = reactive({
	name: "Paul den Boer",
	linkedIn: "https://www.linkedin.com/in/pauwlusdenboer/",
});

let newName = ref(undefined);


let nameLength = computed(() => paulsInfo.name?.length  );
watch(
	() => newName.value,
	() => {
		console.log(newName.value);
	}
);
onMounted(() => paulsInfo.github = "https://www.github.com/Pauldb-Levarne"  )
</script>
<template lang="pug">
.about-paul
  h1 {{ paulsInfo.name }}
  a(:href='paulsInfo.github') Click here for my Github
  br
  a(:href='paulsInfo.linkedIn') Click here for my LinkedIn
  br
  .enter-values
    input(type="text" placeholder="Enter a new name" v-model='newName')
    button(@click="paulsInfo.name = newName " :disabled='newName === undefined') Change the name!

</template>
<style lang="scss" scoped>
.about-paul {
	font-family: "Open Sans";
	h1 {
		font-size: 4rem;
	}
}
</style>
