<script setup lang="ts">
defineOptions({
  name: 'IndexPage',
})
const user = useUserStore()
const name = ref(user.savedName)

const router = useRouter()
function go() {
  if (name.value)
    router.push(`/hi/${encodeURIComponent(name.value)}`)
}

const { t } = useI18n()
</script>

<template>
  <div>
    <div text-4xl>
      <!--      <div i-carbon-campsite inline-block /> -->
      <div inline-block>
        <svg
          class="my-logo" xmlns="http://www.w3.org/2000/svg"
          width="500" height="500" viewBox="-40 -40 80 80"
        >
          <circle r="39" />
          <path d="M0,38a38,38 0 0 1 0,-76a19,19 0 0 1 0,38a19,19 0 0 0 0,38" fill="#fff" />
          <circle cy="19" r="5" fill="#fff" />
          <circle cy="-19" r="5" />
        </svg>
      </div>
    </div>
    <p>
      <em text-sm opacity-75>{{ t('intro.desc') }}</em>
    </p>

    <div py-4 />

    <TheInput
      v-model="name"
      :placeholder="t('intro.whats-your-name')"
      autocomplete="false"
      @keydown.enter="go"
    />
    <label class="hidden" for="input">{{ t('intro.whats-your-name') }}</label>

    <div>
      <button
        m-3 text-sm btn
        :disabled="!name"
        @click="go"
      >
        {{ t('button.go') }}
      </button>
    </div>
  </div>
</template>

<route lang="yaml">
meta:
layout: home
</route>
