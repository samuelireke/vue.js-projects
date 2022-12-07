<script setup>
    import {defineProps, ref} from "vue"
    
    const clipboardAlert = ref(false)

    const p = defineProps(["isWithColour","clipboardAlert"])

    const copyUrl = async (url)=> {
        await navigator.clipboard.writeText(url)
    }
    // reset alert to false
    const resetAlert = () => {
        clipboardAlert = false
     }
    const clipboardAlertReset = setTimeout(resetAlert, 500);
</script>

<template>
    <v-card class="mx-5 my-2 pa-3">
        <div 
            v-if="clipboardAlert"
            class="mb-5">
            <v-dialog
                v-model="clipboardAlert" > 
                <v-alert
                    v-model="clipboardAlert"
                    type="success"
                    closable >
                    Image URL copied to clipboard!
                </v-alert>
            </v-dialog>   
        </div>
        <v-row>
            <v-col
                v-for="n in 204"
                cols = "4"
                sm="3"
                md="3"
                lg="2">
                <v-hover 
                    v-slot="{isHovering,props}">
                    <v-card
                        :elevation="isHovering ?12:2"
                        v-bind="props"
                        @click="copyUrl(`https://picsum.photos/500/300?image=${n * 5 + 10}${p.isWithColour ? '' : '&grayscale'}`); clipboardAlert = true ; clipboardAlertReset">
                        <v-img 
                        :src="`https://picsum.photos/500/300?image=${n * 5 + 10}${p.isWithColour ? '' : '&grayscale'}`"
                        :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}${p.isWithColour ? '' : '&grayscale'}`"
                        aspect-ratio="1"
                        cover>
                            <template v-slot:placeholder>
                                <v-row
                                    class="fill-height ma-0"
                                    align="center"
                                    justify="center">
                                    <v-progress-circular
                                        indeterminate
                                        color="grey-lighten-5">
                                    </v-progress-circular>
                                </v-row>
                            </template>
                        </v-img>
                    </v-card>
                </v-hover>
            </v-col>
        </v-row>
    </v-card>
</template>