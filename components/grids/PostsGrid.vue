<template>
  <resource-grid
    v-bind="$props"
    :resource="$cms.post"
    :theme="$siteConfig.posts.theme || $siteConfig.cards.theme || null"
  >
    <template v-slot:default="{ item }">
      <post-card
        :title="item.title"
        :link="`/${item.slug}`"
        :image="item.featureImage"
        :author="item.author"
        :date="item.date"
      />
    </template>
  </resource-grid>
</template>

<script>
import ResourceGrid from './ResourceGrid'
import PostCard from '~/components/cards/PostCard'
export default {
  components: { ResourceGrid, PostCard },
  props: {
    perRow: { type: Number, default: 3 },
    number: { type: Number, default: 0 },
    order: { type: String, default: 'DESC' },
    category: {
      type: Array,
      default() {
        return []
      }
    },
    exclude: { type: String, default: '' }
  }
}
</script>
