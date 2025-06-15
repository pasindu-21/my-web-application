<template>
  <q-page class="q-pa-md">
    <q-card class="q-mb-md">
      <q-card-section>
        <div class="text-h4 text-primary">About Our Hotel</div>
        <p class="text-body1">Welcome to our luxury hotel, where comfort meets elegance.</p>
      </q-card-section>
    </q-card>

    <!-- Vision & Mission -->
    <q-card class="q-mb-md">
      <q-card-section>
        <div class="text-h5">Our Vision & Mission</div>
        <p class="text-body2">
          We aim to provide world-class hospitality with a touch of home.
        </p>
      </q-card-section>
    </q-card>

    <!-- Services -->
    <q-card class="q-mb-md">
      <q-card-section>
        <div class="text-h5">Our Services</div>
        <q-list bordered separator>
          <q-item v-for="(service, index) in services" :key="index">
            <q-item-section avatar>
              <q-icon :name="service.icon" color="primary" />
            </q-item-section>
            <q-item-section>
              <q-item-label>{{ service.name }}</q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-card-section>
    </q-card>

    <!-- Testimonials -->
    <q-card class="q-mb-md">
      <q-card-section>
        <div class="text-h5">What Our Guests Say</div>
        <q-carousel animated v-model="testimonialIndex" arrows control-color="primary">
          <q-carousel-slide
            v-for="(testimonial, index) in testimonials"
            :key="index"
            class="column flex-center"
          >
            <q-avatar size="56px">
              <img :src="testimonial.image" />
            </q-avatar>
            <p class="q-mt-md text-center text-body1">
              "{{ testimonial.message }}"
            </p>
            <p class="text-bold">{{ testimonial.name }}</p>
          </q-carousel-slide>
        </q-carousel>
      </q-card-section>
    </q-card>

    <!-- Contact Section -->
    <q-card class="q-mb-md">
      <q-card-section>
        <div class="text-h5">Contact Us</div>
        <p>Email: contact@hotel.com</p>
        <p>Phone: +123 456 7890</p>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      services: [
        { name: "Luxury Rooms", icon: "hotel" },
        { name: "Spa & Wellness", icon: "spa" },
        { name: "Conference Halls", icon: "meeting_room" },
        { name: "24/7 Room Service", icon: "room_service" },
      ],
      testimonials: [
        {
          name: "John Doe",
          message: "A fantastic stay with excellent hospitality!",
          image: "https://randomuser.me/api/portraits/men/1.jpg",
        },
        {
          name: "Jane Smith",
          message: "Absolutely loved the experience. Highly recommended!",
          image: "https://randomuser.me/api/portraits/women/2.jpg",
        },
      ],
      testimonialIndex: 0,
    };
  },
};
</script>
