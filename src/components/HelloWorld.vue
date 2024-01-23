<script setup lang="ts">
import { ref } from "vue";
import { useToast } from "nuxt-ui-vue";

const toast = useToast();

defineProps<{ msg: string }>();

const count = ref(0);

const showToaster = () => {
  toast.add({
    title: "Update downloaded.",
    description: "It will be installed on restart. Restart now?",
    icon: "octicon:desktop-download-24",
  });
};
const people = [
  {
    id: 1,
    name: "Lindsay Walton",
    title: "Front-end Developer",
    email: "lindsay.walton@example.com",
    role: "Member",
  },
  {
    id: 2,
    name: "Courtney Henry",
    title: "Designer",
    email: "courtney.henry@example.com",
    role: "Admin",
  },
  {
    id: 3,
    name: "Tom Cook",
    title: "Director of Product",
    email: "tom.cook@example.com",
    role: "Member",
  },
  {
    id: 4,
    name: "Whitney Francis",
    title: "Copywriter",
    email: "whitney.francis@example.com",
    role: "Admin",
  },
  {
    id: 5,
    name: "Leonard Krasner",
    title: "Senior Designer",
    email: "leonard.krasner@example.com",
    role: "Owner",
  },
  {
    id: 6,
    name: "Floyd Miles",
    title: "Principal Designer",
    email: "floyd.miles@example.com",
    role: "Member",
  },
];

const toggle = ref(false);

const page = ref(1);
const items = ref(Array(55));

const tabs = [
  {
    label: "Tab1",
    content: "This is the content shown for Tab1",
  },
  {
    label: "Tab2",
    disabled: true,
    content: "And, this is the content for Tab2",
  },
  {
    label: "Tab3",
    content: "Finally, this is the content for Tab3",
  },
];

const isOpen = ref(false);
const isSlide = ref(false);

const peoples = [
  "Wade Cooper",
  "Arlene Mccoy",
  "Devon Webb",
  "Tom Cook",
  "Tanya Fox",
  "Hellen Schmidt",
  "Caroline Schultz",
  "Mason Heaney",
  "Claudie Smitham",
  "Emil Schaefer",
];

const selected = ref(peoples[0]);

const icons = [
  "ph:alarm-duotone",
  "mdi:adobe",
  "ic:baseline-ac-unit",
  "solar:accessibility-line-duotone",
  "tabler:brand-meta",
  "carbon:asset-confirm",
  "lucide:arrow-up-right-from-circle",
  "system-uicons:calendar-move",
  "uim:history",
];
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
  </div>

  <UButton
    label="Show toast"
    :ui="{ rounded: 'rounded-full' }"
    @click="showToaster"
  />
  <br />
  <div class="flex items-center space-x-3">
    <UIcon v-for="(icon, idx) in icons" :key="idx" :name="icon" size="2xl" />
  </div>
  <UTable :rows="people" />
  <pre>Toggle: {{ toggle }}</pre>
  <UToggle v-model="toggle" />
  <br />
  <UPagination v-model="page" :page-count="5" :total="items?.length ?? 0" />
  <br />
  <UTabs :items="tabs" />
  <br />
  <div>
    <UButton label="Open" @click="isOpen = true" />

    <UModal v-model="isOpen" :transition="false">
      <div class="p-4">
        <UPagination
          v-model="page"
          :page-count="5"
          :total="items?.length ?? 0"
        />
      </div>
    </UModal>
  </div>
  <br />
  <div>
    <UButton label="Open slideover" @click="isSlide = true" />

    <USlideover v-model="isSlide">
      <div class="p-4 flex-1">
        <Placeholder class="h-full" />
      </div>
    </USlideover>
  </div>
  <br />
  <UAvatar
    chip-color="primary"
    chip-text=""
    chip-position="top-right"
    size="sm"
    src="https://avatars.githubusercontent.com/u/739984?v=4"
    alt="Avatar"
  />
  <br />
  <USelectMenu v-model="selected" :options="peoples" />
  <br />
  <div class="flex items-center space-x-4">
    <USkeleton class="h-12 w-12" :ui="{ rounded: 'rounded-full' }" />
    <div class="space-y-2">
      <USkeleton class="h-4 w-[250px]" />
      <USkeleton class="h-4 w-[200px]" />
    </div>
  </div>
  <br />
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
