<template>
  <div class="link-body">
    <template v-if="monthLink">
      <h1>Link of the month</h1>
      <a
        :href="monthLink.url"
        target="_blank"
      >
        {{ monthLink.title }}
      </a>
    </template>
    <div
      v-else
      class="empty"
    >
      Monthly link doesn't exist.
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mockData: [
        {
          url: 'https://hubstaff.com/',
          title: 'One app to automate time tracking processes, workforce management, and productivity metrics.',
          months: [8, 9]
        },
        {
          url: 'https://github.com/',
          title: 'The AI-powered developer platform to build, scale, and deliver secure software.',
          months: [8, 9, 10]
        }
      ],
      monthLink: null
    }
  },
  mounted() {
    this.getMonthLink();
  },
  methods: {
    getMonthLink() {
      const currentMonth = new Date().getMonth() + 1;
      this.monthLink = this.mockData.find(link => link.months.includes(currentMonth));
    }
  }
}
</script>

<style scoped lang="scss">
.link-body {
  padding: 1rem;
  max-width: 500px;
  display: flex;
  flex-direction: column;

  .empty {
    font-weight: bold;
  };

  h1 {
    font-size: 30px;
    font-weight: bold;
  }

  a {
    font-size: 16px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    max-width: 100%;
    color: red;
    text-decoration: underline;

    &:hover {
      opacity: 0.6;
    }
  }
}
</style>
