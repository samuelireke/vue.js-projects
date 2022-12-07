<script setup>
import { defineEmits } from 'vue'

const emits = defineEmits(['selectOption'])

const selectOption = (isColour) => {
    emits("selectOption",isColour)
}
</script>

<template>
    <v-navigation-drawer
        expand-on-hover
        rail
        permanent
      >
        <v-list>
          <v-list-item
            prepend-avatar="https://randomuser.me/api/portraits/men/85.jpg"
            title="John Doe"
            subtitle="johndoe@emailcom"
          ></v-list-item>
        </v-list>

        <v-divider></v-divider>

        <v-list density="compact" nav>
            <v-list-item prepend-icon="mdi-image" 
                title="Colour Gallery" 
                value="colour" 
                @click="selectOption(true)" 
            />
            <v-list-item 
                prepend-icon="mdi-dialpad" 
                title="Greyspace Gallery" 
                value="color" 
                @click="selectOption(false)"
            />
        </v-list>
      </v-navigation-drawer>

</template>
