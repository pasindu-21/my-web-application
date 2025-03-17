<template>
  <q-page>
    <q-carousel swipeable animated v-model="slide" thumbnails infinite>
      <q-carousel-slide :name="1" img-src="https://cdn.quasar.dev/img/mountains.jpg" />
      <q-carousel-slide :name="2" img-src="https://cdn.quasar.dev/img/parallax1.jpg" />
      <q-carousel-slide :name="3" img-src="https://cdn.quasar.dev/img/parallax2.jpg" />
      <q-carousel-slide :name="4" img-src="https://cdn.quasar.dev/img/quasar.jpg" />
    </q-carousel>

    <div class="row">
      <div class="col" v-for="(card, index) in cards" :key="index">
        <div class="q-pa-md row items-start q-gutter-md">
          <q-card :ref="el => cardRefs[index] = el" class="my-card" flat bordered>
            <q-img src="https://cdn.quasar.dev/img/parallax2.jpg" />

            <q-card-section>
              <div class="text-overline text-orange-9">Overline</div>
              <div class="text-h5 q-mt-sm q-mb-xs">Title {{ index + 1 }}</div>
              <div class="text-caption text-grey">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
              </div>
            </q-card-section>

            <q-card-actions>
              <q-btn flat color="primary" label="Share" />
              <q-btn flat color="secondary" label="Book" />

              <q-space />

              <q-btn
                color="grey"
                round
                flat
                dense
                :icon="expandedIndex === index ? 'keyboard_arrow_up' : 'keyboard_arrow_down'"
                @click="toggleExpand(index)"
              />
            </q-card-actions>

            <q-slide-transition>
              <div v-show="expandedIndex === index">
                <q-separator />
                <q-card-section class="text-subtitle2">
                  {{ lorem }}
                </q-card-section>
                <q-space style="height: 20px;"></q-space> 
              </div>
            </q-slide-transition>
          </q-card>
        </div>
      </div>
    </div>
  </q-page>
</template>

<script>
import { ref, nextTick } from 'vue';

export default {
  setup() {
    const expandedIndex = ref(null);
    const cardRefs = ref([]);

    function toggleExpand(index) {
      expandedIndex.value = expandedIndex.value === index ? null : index;

      // Wait for the UI to update, then scroll
      nextTick(() => {
        if (expandedIndex.value !== null && cardRefs.value[index]) {
          cardRefs.value[index].scrollIntoView({
            behavior: 'smooth',
            block: 'start',
          });
        }
      });
    }

    return {
      slide: ref(1),
      expandedIndex,
      toggleExpand,
      cardRefs,
      lorem:
        'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.',
      cards: Array(3).fill({}),
    };
  },
};
</script>
