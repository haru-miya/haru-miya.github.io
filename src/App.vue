<template>
  <v-app :theme="isDark ? 'dark' : 'light'">
    <v-app-bar flat class="px-2 px-md-6">
      <v-app-bar-title class="font-weight-bold">Haruyuki Miyatake</v-app-bar-title>
      <v-spacer />
      <div class="d-none d-md-flex align-center ga-2">
        <v-btn v-for="item in navItems" :key="item.value" variant="text" @click="scrollTo(item.value)">
          {{ item.label }}
        </v-btn>
      </div>
      <v-btn icon variant="text" @click="isDark = !isDark" :aria-label="isDark ? 'light mode' : 'dark mode'">
        <v-icon>{{ isDark ? 'mdi-weather-sunny' : 'mdi-moon-waning-crescent' }}</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <v-container class="py-8 py-md-12">
        <section id="hero" class="mb-10">
          <v-card class="rounded-xl rounded-2xl overflow-hidden" elevation="8">
            <v-row no-gutters>
              <v-col cols="12" md="4" class="hero-pane d-flex align-center justify-center pa-8 pa-md-10">
                <div class="text-center">
                  <v-avatar size="160">
                    <v-img src="/images/icon_yomi.png" alt="アイコン" cover />
                  </v-avatar>
                  <div class="text-h4 font-weight-bold">Haruyuki Miyatake</div>
                  <div class="text-subtitle-1 mt-2 opacity-90">宮武 晴雪</div>
                  <v-chip class="mt-4" color="white" text-color="indigo-darken-3" variant="flat">
                    Student Engineer Portfolio
                  </v-chip>
                </div>
              </v-col>

              <v-col cols="12" md="8" class="pa-6 pa-md-10">
                <div class="text-overline text-indigo-darken-2">ABOUT ME</div>
                <h1 class="text-h5 text-md-h4 mb-4">
                  情報通信・機械学習・エンタメを横断して、
                  作ることを楽しむ学生です。
                </h1>

                <v-row>
                  <v-col cols="12" sm="6">
                    <v-list density="comfortable" bg-color="transparent">
                      <v-list-item prepend-icon="mdi-school" title="大学" subtitle="東京科学大学（旧：東京工業大学）" />
                      <v-list-item prepend-icon="mdi-school-outline" title="専攻" subtitle="工学院情報通信系" />
                      <v-list-item prepend-icon="mdi-flask-outline" title="研究室" subtitle="西尾研究室" />
                      <v-list-item prepend-icon="mdi-calendar" title="入学" subtitle="2023年4月" />
                      <v-list-item prepend-icon="mdi-lightbulb-outline" title="興味分野" subtitle="機械学習 / 通信 / エンタメ / 人間工学" />
                    </v-list>
                  </v-col>
                  <v-col cols="12" sm="6">
                    <div class="d-flex flex-wrap ga-2">
                      <v-chip v-for="tag in tags" :key="tag" color="indigo" variant="tonal">{{ tag }}</v-chip>
                    </div>
                  </v-col>
                </v-row>

                <div class="d-flex flex-wrap ga-3 mt-6">
                  <v-btn color="indigo-darken-2" href="https://github.com/haru-miya" target="_blank" rel="noopener">
                    GitHub
                  </v-btn>
                  <v-btn variant="outlined" color="indigo-darken-2" href="https://atcoder.jp/users/yomi1" target="_blank" rel="noopener">
                    AtCoder
                  </v-btn>
                  <v-btn variant="outlined" color="indigo-darken-2" href="https://www.openbadge-global.com/ns/portal/openbadge/public/assertions/user/SHpOdUZqWEVwd1dmeFJhd1FqTHg4UT09" target="_blank" rel="noopener">
                    Open Badge
                  </v-btn>
                </div>
              </v-col>
            </v-row>
          </v-card>
        </section>

        <section id="profile" class="mb-10">
          <SectionTitle title="Profile" />
          <v-row>
            <v-col cols="12" md="4">
              <v-card class="rounded-xl rounded-2xl h-100">
                <v-card-title>所属・活動</v-card-title>
                <v-card-text>
                  <ul class="pl-5">
                    <li>東京科学大学 工学院情報通信系 西尾研究室</li>
                    <li><a href="https://titech.info/circle/150" target="_blank" rel="noopener">Ultech</a></li>
                    <li><a href="https://portfolio.trap.jp/" target="_blank" rel="noopener">東京科学大学デジタル創作同好会 traP</a></li>
                  </ul>
                </v-card-text>
              </v-card>
            </v-col>

            <v-col cols="12" md="4">
              <v-card class="rounded-xl rounded-2xl h-100">
                <v-card-title>資格・実績</v-card-title>
                <v-card-text>
                  <ul class="pl-5">
                    <li>TOEIC L&amp;R 895点（2026年2月）</li>
                    <li>普通自動車第一種運転免許（2023年9月）</li>
                    <li>ICPC 2025 国内予選 95位</li>
                    <li>GCI 2025 Summer 修了</li>
                  </ul>
                  <v-btn class="mt-3" size="small" variant="text" color="indigo" href="/pdf/修了証.pdf" target="_blank">
                    修了証を見る
                  </v-btn>
                </v-card-text>
              </v-card>
            </v-col>

            <v-col cols="12" md="4">
              <v-card class="rounded-xl rounded-2xl h-100">
                <v-card-title>趣味</v-card-title>
                <v-card-text>
                  <ul class="pl-5">
                    <li>VTuber鑑賞（にじさんじ、ホロライブ など）</li>
                    <li>音楽鑑賞（優里、Mrs. GREEN APPLE、GRe4N BOYZ など）</li>
                  </ul>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </section>

        <section id="research" class="mb-10">
          <SectionTitle title="Research" />
          <v-row>
            <v-col cols="12" md="6">
              <v-card class="rounded-xl rounded-2xl h-100" elevation="3">
                <v-card-item>
                  <template #prepend>
                    <v-avatar color="indigo-lighten-5">
                      <v-icon color="indigo-darken-2">mdi-flask-outline</v-icon>
                    </v-avatar>
                  </template>
                  <v-card-title>研究室</v-card-title>
                  <v-card-subtitle>Laboratory</v-card-subtitle>
                </v-card-item>
                <v-card-text>
                  <div class="text-body-1 font-weight-medium mb-2">西尾研究室</div>
                  <div class="text-body-2 text-medium-emphasis mb-4">東京科学大学 工学院 情報通信系</div>
                  <v-btn color="indigo" variant="text" href="https://nishio-laboratory.github.io/" target="_blank" rel="noopener">
                    研究室サイト
                  </v-btn>
                </v-card-text>
              </v-card>
            </v-col>

            <v-col cols="12" md="6">
              <v-card class="rounded-xl rounded-2xl h-100" elevation="3">
                <v-card-item>
                  <template #prepend>
                    <v-avatar color="indigo-lighten-5">
                      <v-icon color="indigo-darken-2">mdi-wifi</v-icon>
                    </v-avatar>
                  </template>
                  <v-card-title>研究テーマ</v-card-title>
                  <v-card-subtitle>Research Topic</v-card-subtitle>
                </v-card-item>
                <v-card-text>
                  <div class="text-body-1 font-weight-medium mb-2">CSIセンシング (Channel State Information Sensing)</div>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </section>


        <section id="projects" class="mb-10">
          <SectionTitle title="Projects" />
          <v-row>
            <v-col v-for="project in projects" :key="project.title" cols="12" md="6">
              <v-card class="rounded-xl rounded-2xl h-100" elevation="3">
                <v-card-item>
                  <template #prepend>
                    <v-avatar color="indigo-lighten-5">
                      <v-icon color="indigo-darken-2">{{ project.icon }}</v-icon>
                    </v-avatar>
                  </template>
                  <v-card-title>{{ project.title }}</v-card-title>
                  <v-card-subtitle>{{ project.stack }}</v-card-subtitle>
                </v-card-item>
                <v-card-text>
                  <div class="mb-3">{{ project.description }}</div>
                  <div class="text-body-2 text-medium-emphasis">{{ project.role }}</div>
                </v-card-text>
                <v-card-actions>
                  <v-btn v-for="link in project.links" :key="link.label" variant="text" color="indigo" :href="link.href" target="_blank" rel="noopener">
                    {{ link.label }}
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-col>
          </v-row>
        </section>

        <section id="skills" class="mb-10">
          <SectionTitle title="Skills" />
          <v-row>
            <v-col cols="12" md="6">
              <v-card class="rounded-xl rounded-2xl h-100">
                <v-card-title>主な使用言語</v-card-title>
                <v-card-text>
                  <v-list density="compact" bg-color="transparent">
                    <v-list-item title="C++" subtitle="競技プログラミング" prepend-icon="mdi-code-tags" />
                    <v-list-item title="Python" subtitle="機械学習" prepend-icon="mdi-language-python" />
                  </v-list>
                </v-card-text>
              </v-card>
            </v-col>
            <v-col cols="12" md="6">
              <v-card class="rounded-xl rounded-2xl h-100">
                <v-card-title>関心キーワード</v-card-title>
                <v-card-text class="d-flex flex-wrap ga-2">
                  <v-chip v-for="keyword in interestKeywords" :key="keyword" variant="outlined">{{ keyword }}</v-chip>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </section>

        <section id="links" class="mb-4">
          <SectionTitle title="Links" />
          <v-row>
            <v-col v-for="link in links" :key="link.label" cols="12" sm="6" md="4">
              <v-card class="rounded-xl rounded-2xl h-100">
                <v-card-item>
                  <template #prepend>
                    <v-icon color="indigo-darken-2">{{ link.icon }}</v-icon>
                  </template>
                  <v-card-title>{{ link.label }}</v-card-title>
                  <v-card-subtitle>{{ link.description }}</v-card-subtitle>
                </v-card-item>
                <v-card-actions>
                  <v-btn color="indigo" variant="text" :href="link.href" target="_blank" rel="noopener">
                    Open
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-col>
          </v-row>
        </section>
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
import { ref, defineComponent, h } from 'vue'

const isDark = ref(false)

const navItems = [
  { label: 'Profile', value: 'profile' },
  { label: 'Research', value: 'research' },
  { label: 'Projects', value: 'projects' },
  { label: 'Skills', value: 'skills' },
  { label: 'Links', value: 'links' },
]

const tags = ['C++', 'Python', 'Machine Learning', 'Audio', 'Entertainment', 'Competitive Programming']

const interestKeywords = ['機械学習', '通信', 'エンタメ', 'ガジェット', '競技プログラミング']

const projects = [
  {
    title: 'イカンデミンドコントロール',
    stack: 'Unity / C# / Game Development',
    icon: 'mdi-gamepad-variant-outline',
    description: 'サークルのハッカソンで開発したゲーム。',
    role: 'シューティング部分（ギミックなど）の実装を担当。',
    links: [
      { label: 'ゲーム', href: 'https://napolin.github.io/IkanDemindControl/' },
      { label: '開発ブログ', href: 'https://trap.jp/post/1903/' },
    ],
  },
  {
    title: '首都圏外郭放水路 × Minecraft',
    stack: 'Minecraft / JavaScript (Script API)',
    icon: 'mdi-cube-outline',
    description: '株式会社ガリレオ・プロジェクトでのアルバイトで制作。',
    role: 'アドオン制作（ミニゲームなど）を担当。',
    links: [
      { label: '詳細', href: 'https://www.ktr.mlit.go.jp/edogawa/edogawa01318.html' },
      { label: '会社情報', href: 'https://galileo-p.com/' },
    ],
  },
]

const links = [
  {
    label: 'GitHub',
    description: 'コード・制作物',
    href: 'https://github.com/haru-miya',
    icon: 'mdi-github',
  },
  {
    label: 'AtCoder',
    description: '競技プログラミング',
    href: 'https://atcoder.jp/users/yomi1',
    icon: 'mdi-code-braces',
  },
  {
    label: 'Open Badge',
    description: '認定・実績',
    href: 'https://www.openbadge-global.com/ns/portal/openbadge/public/assertions/user/SHpOdUZqWEVwd1dmeFJhd1FqTHg4UT09',
    icon: 'mdi-seal-variant',
  },
]

const scrollTo = (id) => {
  document.getElementById(id)?.scrollIntoView({ behavior: 'smooth', block: 'start' })
}

const SectionTitle = defineComponent({
  name: 'SectionTitle',
  props: {
    title: {
      type: String,
      required: true,
    },
  },
  setup(props) {
    return () =>
      h('div', { class: 'd-flex align-center mb-4' }, [
        h('div', { class: 'text-h5 font-weight-bold' }, props.title),
        h('div', { class: 'flex-grow-1 ms-4 section-divider' }),
      ])
  },
})
</script>

<style scoped>
.hero-pane {
  background: linear-gradient(
    135deg,
    #1a237e 0%,
    #303f9f 40%,
    #5c6bc0 70%,
    #7986cb 100%
  );
  color: white;
}

.profile-avatar {
  border: 4px solid rgba(255, 255, 255, 0.25);
}

.section-divider {
  height: 1px;
  background: rgba(120, 120, 120, 0.25);
}

section {
  scroll-margin-top: 88px;
}

ul {
  margin: 0;
}

a {
  color: inherit;
}
</style>
