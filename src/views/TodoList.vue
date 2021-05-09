<template>
    <main>
        <div class="bg-gray-50">
            <div id="bod">
                <ol>
                    <li v-for="item in items">{{item.todo}}</li>
                </ol>
                <div>
                    <input type="text"  v-model="toadd" />
                    <input type="button" value="Add item" v-on:click="additem" /><br>
                    <input type="number" v-model="toremove" />
                    <input type="button" value="Remove item" v-on:click="removeitem" />
                </div>
            </div>
        </div>
    </main>
</template>

<script setup>
    import { ref } from "vue";
    import ButtonRepo from "@/components/ButtonRepo.vue";
    const toadd = ref("");
    const toremove = ref(1);
    var items = [
        { todo: "Delete these two reminders!" },
        { todo: "Add your own todos!" }
    ];
    const additem = () => {
        items.push({ todo: toadd.value });
        toadd.value = "";
    };
    const removeitem = () => {
        if (toremove.value == "") {
            window.alert("Please enter a number.");
            return;
        };
        let x = toremove.value - 1;
        if (x >= items.length || x < 0) {
            window.alert("Please enter the index of a todo item.");
            return;
        };
        items.splice(x, 1);
        toremove.value = 1; //ok wtf why do I need to do this to make the list update immediately
    };
    /*var engi = new Vue({
        el: "#bod",
        data: {
            items: [
                { todo: "Delete these two reminders!" },
                { todo: "Add your own todos!" }
            ],
        },

        methods: {
            additem() {
                this.items.push({ todo: document.getElementById("toadd").value })
                document.getElementById("toadd").value = ""
            },
            removeitem() {
                if (document.getElementById("toremove").value == "") {
                    window.alert("Please enter a number.")
                    return
                }
                let x = document.getElementById("toremove").value - 1
                if (x >= this.items.length || x < 0) {
                    window.alert("Please enter the index of a todo item.")
                    return
                }
                this.items.splice(x, 1)
            }
        }
    });//*/
</script>