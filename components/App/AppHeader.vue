<template>
  <header>
    <transition name="slide-fade" appear>
      <div class="container">
        <div class="row">
          <div class="col-12">
            <h1>Hi there! 👋 I'm Antoine<span class="is-green">,</span></h1>
            <p>
              a FullStack Developer (TypeScript) <br class="d-block d-md-none">& Vue.js enthusiast based in Paris
              <span class="is-grey-lite">
                <br class="d-none d-md-block">currently working
                <LinkMain
                  href="https://www.liberkeys.com"
                  alt="Liberkeys website"
                  :classes="['green']"
                >
                  <span class="content">@Liberkeys</span>
                </LinkMain>
                <br class="d-none d-md-block">with Vue 2/3, Nuxt, Node and Go.
              </span>
            </p>
          </div>
          <div class="col-12">
            <transition @enter="slideDown" @leave="slideUp">
              <p v-show="active" class="resume">
                Right after getting my <i>Baccalauréat ES with honours</i> in 2012, I started following a licence called
                <LinkMain href="https://humanites.parisnanterre.fr/" alt="Humanités Licence website">"Humanités"</LinkMain> which basically brings five licences in one : <i>Philosophy, French Letters, History, Latin and English</i>.
                <br><br>I've learnt many things throughout my "Humanités" journey but I soon realised that I didn't see myself as a teacher or librairian.
                <br><br>The Internet had always had my attention so I dove right into it. I started coding my personal website for fun and soon began attending a web school called <LinkMain href="https://www.iim.fr/" alt="IIM website">Institut de l'Internet et du Multimédia</LinkMain> (IIM) based in Paris, La Défense. Though that school provided a formation mainly focused on digital project management, I prefered programming. You'll find more info on my <LinkMain href="https://www.linkedin.com/in/antoinepiche/" alt="Linkedin profile">Linkedin profile</LinkMain>.
                <br><br>Since then I've kept improving my skills by teaching myself through Medium articles, documentation reading and online courses (Udemy, Elephorm).
                <br>I'm really committed to my work, learning new things is what really keeps me motivated and I'm obsessed with clean, readable and optimized code. I'm currently working on my back-end skills (and loving it), I'm learning Go and I keep working with Vue.js (or Nuxt.js), of course.
              </p>
            </transition>
            <LinkMain
              alt="Read more"
              :classes="['green readmore']"
              @link-click="readMore"
            >
              <span v-if="!active">Read more</span>
            </LinkMain>
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

@Component
export default class AppHeader extends Vue {
  public active: boolean = false

  public readMore () {
    const s = !this.active
    this.active = !this.active
    return s
  }

  public slideDown (el: any, done: any) {
    (this as any).$velocity(el, 'slideDown', {
      duration: 'fast',
      complete: done,
    })
  }

  public slideUp (el:any, done: any) {
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
    width: 50%;

    @include mobile {
      width: 100%;
    }

    &.resume {
      margin-top: 20px;
      text-align: justify;
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

.is-green {
  color: $apiGreen;
}

.is-grey-lite {
  color: $apiGreyMid;

  a {
    color: $apiGreyMid;
  }
}

</style>
