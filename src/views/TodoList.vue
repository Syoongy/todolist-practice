<template>
    <main>
        <div class="bg-gray-50">
            <div id="bod" class="px-2">
                <ol class="list-decimal list-inside">
                    <li v-for="item in items">{{item.todo}}</li>
                </ol>
                <div class="grid grid-cols-5 gap-2 py-2.5">
                    <div class="col-span-4">
                        <input type="text" v-model="toadd"
                               class="text-sm appearance-none rounded w-full px-3 text-gray-700 bg-gray-200 leading-tight border-none focus:outline-none focus:ring-blue-300 focus:ring-4 h-10" />
                    </div>
                    <div>
                        <input type="button" value="Add item" v-on:click="additem" class="focus:outline-none text-white text-sm py-2.5 px-5 rounded-md bg-blue-500 hover:bg-blue-600 hover:shadow-lg w-full" />
                    </div>
                    <div class="col-span-4">
                        <input type="number" v-model="toremove"
                                class="text-sm appearance-none rounded w-full px-3 text-gray-700 bg-gray-200 leading-tight border-none focus:outline-none focus:ring-blue-300 focus:ring-4 h-10" />
                    </div>
                    <div>
                        <input type="button" value="Remove item" v-on:click="removeitem" class="focus:outline-none text-white text-sm py-2.5 px-5 rounded-md bg-blue-500 hover:bg-blue-600 hover:shadow-lg w-full" />
                    </div>
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
        toremove.value = 0;
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