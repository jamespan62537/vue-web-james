<template>
  <v-app style="background-color: rgb(238, 238, 238);">
    <loading :active.sync="isLoading"></loading>
    <router-view></router-view>
  </v-app>
</template>

<script>
export default {
  data() {
    return {};
  },
  computed: {
    isLoading() {
      return this.$store.state.isLoading;
    }
  }
};
</script>

<style>
html,
body,
div,
span,
applet,
object,
iframe,
h1,
h2,
h3,
h4,
h5,
h6,
p,
blockquote,
pre,
a,
abbr,
acronym,
address,
big,
cite,
code,
del,
dfn,
em,
font,
img,
ins,
kbd,
q,
s,
samp,
small,
strike,
strong,
sub,
sup,
tt,
var,
dl,
dt,
dd,
ol,
ul,
li,
fieldset,
form,
label,
legend,
table,
caption,
tbody,
tfoot,
thead,
tr,
th,
td {
  margin: 0;
  padding: 0;
  border: 0;
  outline: 0;
  font-weight: inherit;
  font-style: inherit;
  font-size: 100%;
  font-family: inherit;
}
/* remember to define focus styles! */
:focus {
  outline: 0;
}
html {
  height: 100%;
}
body {
  min-height: 100%;
  line-height: 1;
  color: black;
  background: white;
}
ol,
ul {
  list-style: none;
}
/* tables still need 'cellspacing="0"' in the markup */
table {
  border-collapse: separate;
  border-spacing: 0;
}
caption,
th,
td {
  text-align: left;
  font-weight: normal;
}
blockquote:before,
blockquote:after,
q:before,
q:after {
  content: "";
}
blockquote,
q {
  quotes: "" "";
}

/* CSS Reset End */

#app {
  font-family: "微軟正黑體";
}
.panel_title {
  font-size: 18px;
}
.panel_content {
  padding-bottom: 24px;
}
</style>
