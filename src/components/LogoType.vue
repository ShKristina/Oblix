<template>
  <div class="v-logo-type">
    <div class="v-logo-type__line-before"></div>

    <div class="v-logo-type__svg">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 107.941 48.489">
        <g data-name="Group 1409">
          <path data-name="Path 1087" d="M12.02 24.449a12.02 12.02 0 1 0 12.02 12.02 12.02 12.02 0 0 0-12.02-12.02zm0 21.093a9.074 9.074 0 1 1 9.074-9.074 9.074 9.074 0 0 1-9.074 9.074z" fill="#1f1917"></path>
          <path data-name="Path 1088" d="M40.301 24.449a12.02 12.02 0 1 0 12.02 12.02 12.02 12.02 0 0 0-12.02-12.02zm0 21.093a9.074 9.074 0 1 1 9.074-9.074 9.074 9.074 0 0 1-9.074 9.074z" fill="#1f1917"></path>
          <path data-name="Rectangle 1572" fill="#1f1917" d="M81.795 26.514l2.225-2.225 21.931 21.93-2.225 2.226z"></path>
          <path data-name="Rectangle 1573" fill="#1f1917" d="M69.643 24.331h5.774v24.157h-5.774z"></path>
          <path data-name="Rectangle 1574" fill="#1f1917" d="M56.916.057h5.774v48.432h-5.774z"></path>
          <path data-name="Rectangle 1575" fill="#1f1917" d="M84.019 48.445l-2.225-2.225 21.93-21.931 2.226 2.225z"></path>
          <path data-name="Line 211" fill="#1f1917" d="M71.293 24.275h36.648"></path>
          <path data-name="Line 212" fill="#1f1917" d="M59.391 0H23.332"></path>
          <path data-name="Path 1089" d="M34.055 29.824V0h-5.774v36.295h2.946a9 9 0 0 1 2.828-6.471z" fill="#1f1917"></path>
        </g>
      </svg>
    </div>

    <div class="v-logo-type__line-after"></div>
  </div>
</template>

<script>
export default{
  name:'LogoType'
}
</script>

<style lang="scss">
.v-logo-type {
  display: flex;

  &__svg {
    flex: 30%;
    margin: -10px auto -7px auto ;
    display: flex;
    justify-content: center;
  }

  &__line-before, &__line-after {
    border-bottom: 2px solid $light-gray-color;
    flex: 40%;
    margin-bottom: 16px;
  }
}
</style>