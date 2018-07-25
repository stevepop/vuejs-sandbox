<template>
    <div class="list-group">
         <li 
            class="list-group-item"
            v-for="link in links" 
            :key="link.title">
            <slot name="link"
                :link="link"
            >
            </slot>
    </li>
    </div>
</template>

<script>
export default {
   data() {
    return {
      links: [
        { href: 'http://google.com', title: 'First Link', bookmarked: true },
        { href: 'http://twitter.com', title: 'Second Link', bookmarked: false },
        { href: 'http://facebook.com', title: 'Third Link', bookmarked: true },
        { href: 'http://yahoo.com', title: 'Fourth Link', bookmarked: false },
      ]
    }
  } 
}
</script>

