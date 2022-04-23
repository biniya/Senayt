<script>
import ThemeSwitcher from "../ThemeSwitcher";
// import HireMeModal from "../HireMeModal.vue";
import feather from "feather-icons";
import AppHeaderLinks from "./AppHeaderLinks.vue";
import Button from "../reusable/Button.vue";

export default {
  components: {
    ThemeSwitcher,
    // HireMeModal,
    AppHeaderLinks,
    Button,
  },
  data() {
    return {
      isOpen: false,
      theme: "",
      modal: false,
      categories: [
        {
          id: 1,
          value: "web",
          name: "Web Application",
        },
        {
          id: 2,
          value: "mobile",
          name: "Mobile Application",
        },
        {
          id: 3,
          value: "ui-ux",
          name: "UI/UX Design",
        },
        {
          id: 4,
          value: "branding",
          name: "Branding & Anim",
        },
      ],
    };
  },

  created() {
    this.theme = localStorage.getItem("theme") || "light";
  },
  mounted() {
    feather.replace();
    this.theme = localStorage.getItem("theme") || "light";
  },
  methods: {
    updateTheme(theme) {
      this.theme = theme;
    },
    showModal() {
      if (this.modal) {
        // Stop screen scrolling
        document
          .getElementsByTagName("html")[0]
          .classList.remove("overflow-y-hidden");
        this.modal = false;
      } else {
        document
          .getElementsByTagName("html")[0]
          .classList.add("overflow-y-hidden");
        this.modal = true;
      }
    },
  },
  updated() {
    feather.replace();
  },
};
</script>

<template>
  <nav id="nav" class="sm:container sm:mx-auto">
    <!-- Header start -->
    <div
      class="z-10 max-w-screen-lg xl:max-w-screen-xl block sm:flex sm:justify-between sm:items-center my-6"
    >
      <!-- Header menu links and small screen hamburger menu -->
      <div class=" flex justify-between items-center px-4 sm:px-0">
        <!-- Header logos -->
        <div>
          <router-link to="/">
            <svg
              fill="#000000"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 50 50"
              width="50px"
              height="50px"
            >
              <path
                d="M 25 2 C 12.309288 2 2 12.309297 2 25 C 2 37.690703 12.309288 48 25 48 C 37.690712 48 48 37.690703 48 25 C 48 12.309297 37.690712 2 25 2 z M 25 4 C 36.609833 4 46 13.390175 46 25 C 46 36.609825 36.609833 46 25 46 C 13.390167 46 4 36.609825 4 25 C 4 13.390175 13.390167 4 25 4 z M 25 6 C 14.518428 6 6 14.518436 6 25 C 6 35.481564 14.518428 44 25 44 C 35.481572 44 44 35.481564 44 25 C 44 14.518436 35.481572 6 25 6 z M 25 8 C 34.400692 8 42 15.599314 42 25 C 42 34.400686 34.400692 42 25 42 C 15.599308 42 8 34.400686 8 25 C 8 15.599314 15.599308 8 25 8 z M 24.757812 10.998047 C 22.2533 10.998047 19.685759 11.645653 17.662109 12.96875 C 15.63846 14.291847 14.152344 16.39657 14.152344 19.042969 C 14.152344 22.188667 15.929733 24.279487 18.15625 25.472656 C 20.382767 26.665825 23.063701 27.16896 25.365234 27.664062 C 27.524302 28.128357 28.811458 28.622894 29.433594 29.076172 C 30.055729 29.52945 30.152257 29.817534 30.158203 30.574219 C 30.163003 31.171487 29.839396 31.742781 29.013672 32.261719 C 28.187948 32.780657 26.884763 33.158203 25.261719 33.158203 C 23.331662 33.158203 22.007482 32.745435 21.185547 32.017578 C 20.363612 31.289721 19.892578 30.170045 19.892578 28.302734 A 1.0001 1.0001 0 0 0 18.71875 27.318359 L 14.466797 28.064453 A 1.0001 1.0001 0 0 0 13.652344 29.205078 C 14.144368 32.311344 15.39495 34.804898 17.392578 36.488281 C 19.390206 38.171665 22.075656 39 25.261719 39 C 31.527243 39 36 34.884464 36 30.566406 C 36 27.638239 34.610709 25.537528 32.742188 24.244141 C 30.873665 22.950753 28.579144 22.348658 26.503906 21.941406 C 23.694883 21.390385 21.917159 20.881252 20.992188 20.390625 C 20.067214 19.899998 19.994141 19.702166 19.994141 19.042969 C 19.994141 18.125929 20.362157 17.762733 21.230469 17.384766 C 22.098781 17.006798 23.435532 16.841797 24.755859 16.841797 C 26.308341 16.841797 27.367931 17.190583 28.027344 17.78125 C 28.686756 18.371917 29.080078 19.270995 29.080078 20.789062 A 1.0001 1.0001 0 0 0 30.207031 21.78125 L 34.410156 21.244141 A 1.0001 1.0001 0 0 0 35.273438 20.107422 C 34.86193 17.294293 33.706087 14.981352 31.880859 13.398438 C 30.055632 11.815523 27.602744 10.998047 24.757812 10.998047 z M 24.757812 12.998047 C 27.226882 12.998047 29.152791 13.680821 30.570312 14.910156 C 31.768843 15.949572 32.541602 17.505539 32.996094 19.408203 L 30.894531 19.677734 C 30.701987 18.309864 30.265682 17.099339 29.363281 16.291016 C 28.212194 15.259932 26.609378 14.841797 24.755859 14.841797 C 23.291187 14.841797 21.748078 14.977749 20.431641 15.550781 C 19.115203 16.123814 17.994141 17.362008 17.994141 19.042969 C 17.994141 20.278771 18.74041 21.46108 20.054688 22.158203 C 21.368965 22.855326 23.249164 23.339365 26.119141 23.902344 C 28.089903 24.289092 30.139538 24.875309 31.603516 25.888672 C 33.067493 26.902034 34 28.225574 34 30.566406 C 34 33.432348 30.648195 37 25.261719 37 C 22.416782 37 20.255013 36.284851 18.681641 34.958984 C 17.317034 33.809042 16.437468 32.055605 15.919922 29.839844 L 18.080078 29.458984 C 18.280808 31.121664 18.789638 32.566599 19.861328 33.515625 C 21.188643 34.691018 23.048775 35.158203 25.261719 35.158203 C 27.185675 35.158203 28.838099 34.73439 30.078125 33.955078 C 31.318151 33.175766 32.169403 31.952325 32.158203 30.558594 C 32.149103 29.406278 31.670193 28.230456 30.611328 27.458984 C 29.552464 26.687512 28.055042 26.19669 25.787109 25.708984 C 23.458643 25.208087 20.929046 24.688315 19.101562 23.708984 C 17.274079 22.729654 16.152344 21.49927 16.152344 19.042969 C 16.152344 17.118367 17.141259 15.698232 18.755859 14.642578 C 20.37046 13.586925 22.607326 12.998047 24.757812 12.998047 z"
              />
            </svg>
            <h1 class="text-primary-dark text-lg dark:text-white">
              Senayt Lemma
            </h1>
            <!-- <img
							v-if="theme === 'light'"
							src="@/assets/images/logo-dark.svg"
							class="w-36"
							alt="Dark Logo"
						/>
						<img
							v-else
							src="@/assets/images/logo-light.svg"
							class="w-36"
							alt="Light Logo"
						/> -->
          </router-link>
        </div>

        <!-- Theme switcher small screen -->
        <theme-switcher
          :theme="theme"
          @themeChanged="updateTheme"
          class="block sm:hidden bg-ternary-light dark:bg-ternary-dark hover:bg-hover-light dark:hover:bg-hover-dark hover:shadow-sm px-2.5 py-2 rounded-lg"
        />

        <!-- Small screen hamburger menu -->
        <div class="sm:hidden">
          <button
            @click="isOpen = !isOpen"
            type="button"
            class="focus:outline-none"
            aria-label="Hamburger Menu"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              class="h-7 w-7 fill-current text-secondary-dark dark:text-ternary-light"
            >
              <path
                v-if="isOpen"
                fill-rule="evenodd"
                d="M18.278 16.864a1 1 0 0 1-1.414 1.414l-4.829-4.828-4.828 4.828a1 1 0 0 1-1.414-1.414l4.828-4.829-4.828-4.828a1 1 0 0 1 1.414-1.414l4.829 4.828 4.828-4.828a1 1 0 1 1 1.414 1.414l-4.828 4.829 4.828 4.828z"
                clip-rule="evenodd"
              ></path>
              <path
                v-if="!isOpen"
                fill-rule="evenodd"
                d="M4 5h16a1 1 0 0 1 0 2H4a1 1 0 1 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2z"
              ></path>
            </svg>
          </button>
        </div>
      </div>

      <!-- Header links -->
      <AppHeaderLinks :showModal="showModal" :isOpen="isOpen" />

      <!-- Header right section buttons -->
      <div
        class="hidden sm:flex justify-between items-center flex-col md:flex-row"
      >
        <!-- Hire me button -->
        <div class="hidden md:block">
          <!-- <Button
            title="Hire Me"
            class="text-md font-general-medium bg-indigo-500 hover:bg-indigo-600 text-white shadow-sm rounded-md px-5 py-2.5 duration-300"
            @click="showModal()"
            aria-label="Hire Me Button"
          /> -->
          <a href="https://www.upwork.com/freelancers/~01f7e4642718518a48" target="_blank">
          <Button
            title="Hire Me"
            class="text-md font-general-medium bg-indigo-500 hover:bg-indigo-600 text-white shadow-sm rounded-md px-5 py-2.5 duration-300"
            aria-label="Hire Me Button"
          />
          </a>
        </div>

        <!-- Theme switcher large screen -->
        <theme-switcher
          :theme="theme"
          @themeChanged="updateTheme"
          class="ml-8 bg-primary-light dark:bg-ternary-dark px-3 py-2 shadow-sm rounded-xl cursor-pointer"
        />
      </div>
    </div>

    <!-- Hire me modal -->
    <!-- <HireMeModal
      :showModal="showModal"
      :modal="modal"
      :categories="categories"
      aria-modal="Hire Me Modal"
    /> -->
  </nav>
</template>

<style scoped>
#nav a.router-link-exact-active {
  @apply text-indigo-700;
  @apply dark:text-indigo-400;
  @apply font-medium;
}
</style>
