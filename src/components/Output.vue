<template>
    <div class="header flex absolute justify-between items-center">
        <div class="output-section">
            <input type="text" placeholder="Your Password" :value="value" @focus="$event.target.select()" readonly
                ref="myinput" />
        </div>
        <div class="copy-section">
            <span class="copied-span"></span>
            <i @click="copyInput" class="bi bi-clipboard cursor-pointer"></i>
        </div>
    </div>
</template>
    
<script>
export default {
    name: 'Output',
    props: ['value'],
    methods: {
        copyInput() {
            const inputElement = document.createElement("input");   
            inputElement.value = this.passwordInput;
            document.body.appendChild(inputElement);
            inputElement.select();
            document.execCommand("copy");
            document.body.removeChild(inputElement);
            document.querySelector(".copied-span").innerHTML = "COPIED";
            setTimeout(() => {
                document.querySelector(".copied-span").innerHTML = "";
            }, 1000);
        },
    },
};
</script>