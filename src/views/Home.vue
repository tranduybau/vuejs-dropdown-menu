<template>
  <div class="home">
    <div class="spacing">
      <DropdownMenu id="dropdownmenu1" :arrays="arrays">
        DropdownMenu 1
      </DropdownMenu>
    </div>
    <div class="spacing">
      <DropdownMenu id="dropdownmenu2" :arrays="arrays">
        DropdownMenu 2
      </DropdownMenu>
    </div>
  </div>
</template>

<script>
import DropdownMenu from '@/components/DropdownMenu';

export default {
  name: 'Home',
  components: {
    DropdownMenu,
  },
  data() {
    return {
      arrays: [
        {
          text: 'Link 1',
          link: '/about',
        },
        {
          text: 'Link 2',
          link: '/about',
        },
        {
          text: 'Link 3',
          link: '/about',
        },
        {
          text: 'Link 4',
          link: '/about',
        },
        {
          text: 'Link 5',
          link: '/about',
        },
      ],
    };
  },
};
</script>
