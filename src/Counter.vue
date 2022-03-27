<script>
export default {
  props: {
    level: {
      type: Number,
      default: 1,
    },
  },
  data() {
    return {
      count: 0,
    };
  },
  render(h) {
    return h("div", null, [
      h(`h${this.level}`, null, `计数案列:${this.count}`),
      h(
        "button",
        {
          on: {
            click: () => {
              this.count++;
            },
          },
        },
        "+1"
      ),
      h(
        "button",
        {
          on: {
            click: () => {
              this.count--;
            },
          },
        },
        "-1"
      ),
    ]);
  },
};
</script>