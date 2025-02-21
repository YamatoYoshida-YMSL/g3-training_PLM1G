<script setup>
import { useLockScreen } from 'viy-ui';
import { useI18n } from 'vue-i18n';

const { t } = useI18n();
const { lockScreen } = useLockScreen();

defineOptions({
  name: 'frontendtest',
});

const form = ref();

const formData = reactive({
});
</script>

<template>
  <VueForm ref="form" v-loading="lockScreen" :model="formData" />
</template>
