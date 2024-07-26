<template>
  <section class="box comments">
    <hr />
    <h3 class="title is-5">评论 {{ count }}</h3>
    <lv-comments-form :slug="slug" v-if="token" @loadComments="fetchComments"/>

    <lv-comments-item
      v-for="comment in comments"
      :key="`comment-${comment.id}`"
      :comment="comment"
    />
  </section>
</template>

<script>
import { mapGetters } from 'vuex'
import { fetchCommentsByTopicId, fetchCountByTopicId } from '@/api/comment'
import LvCommentsForm from './CommentsForm'
import LvCommentsItem from './CommentsItem'

export default {
  name: 'LvComments',
  components: {
    LvCommentsForm,
    LvCommentsItem
  },
  data() {
    return {
      comments: [],
      count: 0
    }
  },
  props: {
    slug: {
      type: String,
      default: null
    }
  },
  computed: {
    ...mapGetters([
      'token'
    ])
  },
  async mounted() {
    await this.fetchComments(this.slug)
  },
  methods: {
    // 初始化
    async fetchComments(topic_id) {
      console.log(topic_id)
      fetchCountByTopicId(topic_id).then(response => {
        const { data } = response
        this.count = data
      })
      fetchCommentsByTopicId(topic_id).then(response => {
        const { data } = response
        this.comments = data
      })
    }
  }
}
</script>
