<!-- SPDX-License-Identifier: AGPL-3.0-or-later -->
<template>
  <form class="card-style flex w-full flex-col space-y-3 px-5 py-4">
    <h1 class="text-2xl">
      <strong>{{ $t("i18n.components.card_date_picker.date") }} *</strong>
    </h1>
    <div class="flex grow">
      <div class="flex w-[50%] flex-row space-x-2">
        <FormCheckbox />
        <label for="All Day">{{
          $t("i18n.components.card_date_picker.all_day")
        }}</label>
      </div>
      <div class="flex w-[50%] flex-row space-x-2 pl-1">
        <FormCheckbox />
        <label for="Multiple Days">{{
          $t("i18n.components.card_date_picker.multiple_days")
        }}</label>
      </div>
    </div>
    <div class="flex flex-row space-x-2">
      <DatePicker
        v-model="date1"
        mode="Time"
        is24hr
        hide-time-header
        :color="colorModePreference"
        class="date-picker-width elem-shadow-sm bg-layer-2"
      />
      <DatePicker
        v-model="date2"
        mode="Time"
        is24hr
        hide-time-header
        :color="colorModePreference"
        class="date-picker-width elem-shadow-sm bg-layer-2"
      />
    </div>
    <DatePicker
      :first-day-of-week="2"
      trim-weeks
      expanded
      :color="colorModePreference"
      :attributes="attributes"
      transparent
    ></DatePicker>
  </form>
</template>

<script setup lang="ts">
import { DatePicker } from "v-calendar";
import "v-calendar/style.css";

const date1 = "2021-02-28T18:20:00.000Z";
const date2 = "2021-02-28T18:20:00.000Z";

const colorMode = useColorMode();
const colorModePreference = colorMode.preference == "light" ? "light" : "dark";

const attributes = ref([
  {
    highlight: {
      color: "orange",
    },
  },
]);
</script>

<style>
.vc-light {
  /* Base. */
  --vc-border: transparent;
  --vc-hover-bg: rgba(140, 140, 140, 0.2);
  --vc-focus-ring: 0 0 0 2px rgba(242, 166, 84, 1);
  --vc-day-content-hover-bg: rgba(242, 166, 84, 1);
  --vc-accent-600: #d76226;

  /* Time select group. */
  --vc-time-select-group-bg: transparent;
  --vc-time-select-group-border: transparent;
  --vc-time-select-group-icon-color: rgba(0, 0, 0, 0.85);
}
.vc-dark {
  /* Base. */
  --vc-border: transparent;
  --vc-hover-bg: rgba(70, 70, 70, 0.25);
  --vc-focus-ring: 0 0 0 2px rgba(241, 156, 65, 1);
  --vc-day-content-hover-bg: rgba(242, 166, 84, 1);
  --vc-accent-600: #d76226;

  /* Time select group. */
  --vc-time-select-group-bg: transparent;
  --vc-time-select-group-border: transparent;
  --vc-time-select-group-icon-color: rgba(43, 50, 59, 1);
  --vc-day-content-hover-bg: rgba(242, 166, 84, 1);
}

.date-picker-width {
  width: 100%;
}
</style>
