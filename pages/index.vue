<script setup lang="ts">
const locatePath = useLocalePath()
const { t } = useI18n()

const desList = ref([
  {
    icon: 'material-symbols:browse-activity-outline-rounded',
    title: 't1',
    des: 'd1'
  },
  {
    icon: 'material-symbols:speed-outline-rounded',
    title: 't2',
    des: 'd2'
  },
  {
    icon: 'material-symbols:encrypted-outline',
    title: 't3',
    des: 'd3'
  }
])

useSeoMeta({
  title: t('home')
})
</script>

<template>
  <div>
    <div class="pb-12 bg-sky-200 dark:bg-sky-900 pt-24">
      <div class="text-center">
        <h1 class="text-3xl flex flex-row justify-center items-center gap-4">
          <img src="/favicon.webp" alt="web camera" class="size-8" />WebCamera
        </h1>
        <h2 class="text-base mt-8">{{ $t('welcome') }}</h2>
      </div>

      <div class="flex flex-row items-center justify-center gap-8 mt-12">
        <UButton color="violet" size="lg" :to="locatePath('/camera')"
          ><template #leading><Icon name="solar:videocamera-record-outline" /></template
          >{{ $t('btn.camera') }}</UButton
        >

        <UButton color="sky" size="lg" :to="locatePath('/monitor')"
          ><template #leading><Icon name="solar:monitor-camera-line-duotone" /></template
          >{{ $t('btn.monitor') }}</UButton
        >
      </div>
    </div>

    <div class="md:grid md:grid-cols-3 md:p-12 gap-4 p-4 space-y-4 md:space-y-0">
      <div
        v-for="(item, idx) of desList"
        class="flex flex-row items-center md:gap-4 gap-3 p-3 shadow shadow-black/20 rounded-lg bg-white dark:bg-gray-700"
      >
        <Icon :name="item.icon" size="32" />
        <div class="flex-1">
          <h2 class="md:text-xl text-lg">{{ $t('des.' + item.title) }}</h2>
          <p class="md:text-sm text-xs">{{ $t('des.' + item.des) }}</p>
        </div>
      </div>
    </div>
  </div>
</template>
