<script>
export default {
  setup() {
    return {
      bios: [
        {
          id: 1,
          bio: " HI I'M SENAYT",
        },
        {
          id: 2,
          bio:
            "A Front-End Developer passionate about creating interactive applications on the web",
        },
        {
          id: 3,
          bio:
            "I'm expert on HTML and CSS and framworks like Tailwind-CSS, VueJS and exploring new things",
        },
      ],
    };
  },
};
</script>

<template>
  <div class="block sm:flex sm:gap-10 mt-10 sm:mt-20">
    <!-- About profile image -->
    <div class="w-full sm:w-1/4 mb-7 sm:mb-0">
      <img
        src="@/assets/images/Senayt_Lemma.png"
        class="rounded-xl w-96"
        alt=""
      />
    </div>

    <!-- About details -->
    <div class="w-full sm:w-3/4 text-left">
      <p
        v-for="bio in bios"
        :key="bio.id"
        class="font-general-regular mb-4 text-ternary-dark dark:text-ternary-light text-lg"
      >
        {{ bio.bio }}
      </p>
    </div>
  </div>
</template>
