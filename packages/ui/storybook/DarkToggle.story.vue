<script setup lang="ts">
import { isDark as getIsDark, toggleDark } from 'histoire/client'
import { computed } from 'vue'
import DarkToggle from '../src/components/DarkToggle.vue'
import Button from '../src/components/Button.vue'
import Icon from '../src/components/Icon.vue'

const dark = computed({
  get: () => getIsDark(),
  set: (v) => {
    toggleDark(v)
    window.document.documentElement.classList.toggle('dark', v)
  },
})
</script>

<template>
  <Story>
    <Variant title="With Animation">
      <DarkToggle v-model:isDark="dark">
        <template #default="{ toggle, isDark }">
          <Button
            @click="(e) => {
              toggle(e)
            }"
          >
            <Icon :class="isDark.value ? 'i-carbon-moon' : 'i-carbon-sun'" />
          </Button>
        </template>
      </DarkToggle>
    </Variant>
    <Variant title="No Animation">
      <DarkToggle v-model:isDark="dark" :animation="false">
        <template #default="{ toggle, isDark }">
          <Button
            @click="(e) => {
              toggle(e)
            }"
          >
            <Icon :class="isDark.value ? 'i-carbon-moon' : 'i-carbon-sun'" />
          </Button>
        </template>
      </DarkToggle>
    </Variant>
  </Story>
</template>
