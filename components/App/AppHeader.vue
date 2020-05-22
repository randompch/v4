<template>
  <header>
    <transition name="slide-fade" appear>
      <div class="container">
        <div class="row">
          <div class="col-12">
            <h1>Hi! 👋 I'm Antoine Piché<span class="is-green">,</span></h1>
            <p>
              a FullStack Developer (TypeScript) & VueJS enthusiast based in Paris
              <span class="is-grey-lite">
                <br class="d-none d-md-block">currently working at
                <link-main
                  href="https://la-releve.com"
                  alt="La Relève website"
                  :classes="['green']"
                >
                  <span class="content">La Relève</span>
                </link-main>
                <br class="d-none d-md-block">as a FullStack Developer (Nuxt.js, Express, MySQL, Serverless, Go)
              </span>
            </p>
          </div>
          <div class="col-12">
            <transition @enter="slide_down" @leave="slide_up">
              <p v-show="active" class="resume">
                Right after getting my <i>Baccalauréat ES with honours</i> in 2012, I started following a licence called
                <link-main href="https://humanites.parisnanterre.fr/" alt="Humanités Licence website">"Humanités"</link-main> which basically brings five licences in one : <strong>Philosophy, French Letters, History, Latin and English</strong>.
                <br>I've learnt many things throughout my "Humanités" journey but I soon realised that I didn't see myself as a teacher or librairian.
                <br>The Internet had always had my attention so I dove right into it. I started coding my personal website for fun and soon began attending a web school called <link-main href="https://www.iim.fr/" alt="IIM website">Institut de l'Internet et du Multimédia</link-main> (IIM) based in Paris, La Défense. Though that school provided a formation mainly focused on digital project management, I prefered programming. You'll find more info on my <link-main href="https://www.linkedin.com/in/antoinepiche/" alt="Linkedin profile">Linkedin profile</link-main>.
                <br><br>Since then I've kept improving my skills by teaching myself through Medium articles, documentation reading and online courses (Udemy, Elephorm).
                <br>I'm really committed to my work, learning new things is what really keeps me motivated and I'm obsessed with clean, readable and optimized code. I'm currently working on my back-end skills (and loving it), I'm learning Go and I keep working with Vue.js (or Nuxt.js), of course.
              </p>
            </transition>
            <link-main
              alt="Read more"
              :classes="['green readmore']"
              @link-click="readMore"
            >
              <span v-if="!active">Read more</span>
            </link-main>
            <p class="seework">
              Or see my selected works below<span class="is-green">.</span>👇
            </p>
          </div>
        </div>
      </div>
    </transition>
  </header>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'
import LinkMain from '~/components/Link/LinkMain.vue'

@Component({
  components: {
    LinkMain,
  },
})
export default class AppHeader extends Vue {
  public active: boolean = false

  public readMore () {
    const s = !this.active
    this.active = !this.active
    return s
  }

  public slide_down (el: any, done: any) {
    (this as any).$velocity(el, 'slideDown', {
      duration: 'fast',
      complete: done,
    })
  }

  public slide_up (el:any, done: any) {
    (this as any).$velocity(el, 'slideUp', {
      duration: 'fast',
      complete: done,
    })
  }
}
</script>

<style lang="scss" scoped>
header {
  min-height: 80vh;
  display: flex;
  // align-items: center;
  padding-top: 40vh;
  padding-bottom: 2vh;
  background-color: #fcfcfc;

  h1 {
    font-size: rem(28px);
    font-weight: $fsemibold;
  }

  p {
    font-size: rem(18px);

    &.resume {
      margin-top: 20px;
    }

    &.seework {
      display: inline-block;
      font-size: rem(18px);
      margin-top: 20px;
    }
  }

  .readmore {
    margin-top: 20px;
    margin-right: 5px;
  }
}
</style>