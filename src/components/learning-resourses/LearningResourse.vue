<template>
  <li>
    <div>
      <header>
        <h3> {{title}} </h3>
        <button> Delete </button>
      </header>
      <p>{{description}}</p>
      <nav>
        <a :href="link"> {{link}} </a>
      </nav>
    </div>
  </li>
</template>

<script>
export default {
  props: [ 'title', 'description', 'link' ],
}
</script>