<template>
  <section class="nomads-showcase-section">
    <div class="showcase-header">
      <div class="header-left">
        <h2 class="showcase-title">地理知识与人文景观实战模板库</h2>
        <p class="showcase-subtitle">精选自然地貌、气象水文、人文历史与高考研学模板，点击“一键套用”快速解析</p>
      </div>
      <span class="showcase-badge">已收录 {{ showcaseItems.length }} 个地理考察模板</span>
    </div>

    <div class="showcase-grid">
      <div 
        v-for="item in showcaseItems" 
        :key="item.id" 
        class="glass-card showcase-card"
      >
        <div class="card-header">
          <span class="scenario-tag">{{ item.tag }}</span>
          <span class="usage-count">{{ item.usageCount }} 次解析</span>
        </div>

        <div class="card-content">
          <h3 class="item-title">{{ item.title }}</h3>
          <p class="item-prompt">“{{ item.prompt }}”</p>
        </div>

        <div class="card-action">
          <button class="apply-btn" @click="applyTemplate(item)">
            <span>一键套用</span>
            <svg class="arrow-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <line x1="5" y1="12" x2="19" y2="12"></line>
              <polyline points="12 5 19 12 12 19"></polyline>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const emit = defineEmits<{
  (e: 'apply-template', payload: { prompt: string; geoType?: string; geoRegion?: string; perspective?: string }): void;
}>();

export interface ShowcaseItem {
  id: string;
  tag: string;
  title: string;
  prompt: string;
  geoType?: string;
  geoRegion?: string;
  perspective?: string;
  usageCount: string;
}

const showcaseItems = computed<ShowcaseItem[]>(() => [
  {
    id: 'dili-1',
    tag: '自然地貌',
    title: '西南喀斯特溶洞与石林成因演化',
    prompt: '请解析我国西南云贵高原喀斯特地貌（石林、溶洞、暗河）的岩性基础、气候条件与水文侵蚀演化过程。',
    geoType: '自然地理地貌与构造解析',
    geoRegion: '中国地理',
    perspective: '自然科学视角',
    usageCount: '58.4k'
  },
  {
    id: 'dili-2',
    tag: '构造气候',
    title: '青藏高原隆升对东亚季风与水系演变影响',
    prompt: '详细分析青藏高原隆升对东亚季风气候形成、大江大河发源及西北干旱化演变的地质与气象机制。',
    geoType: '自然地理地貌与构造解析',
    geoRegion: '中国地理',
    perspective: '自然科学视角',
    usageCount: '49.1k'
  },
  {
    id: 'dili-3',
    tag: '人文历史',
    title: '江南水乡聚落分布与古镇水运历史地理',
    prompt: '分析太湖流域江南水乡古镇的聚落选址、水网交织下的商业发展及民俗风情的地理环境背景。',
    geoType: '人文地理与城市历史变迁',
    geoRegion: '中国地理',
    perspective: '人文历史视角',
    usageCount: '41.8k'
  },
  {
    id: 'dili-4',
    tag: '高考考点',
    title: '高考地理等高线地形图判读与鞍部陡崖计算',
    prompt: '拆解高考地理等高线地形图常考命题点，包含山脊山谷判读、陡崖相对高度计算及水库坝址选址分析。',
    geoType: '高考地理考点与综合题拆解',
    geoRegion: '中国地理',
    perspective: '高考教研视角',
    usageCount: '63.2k'
  },
  {
    id: 'dili-5',
    tag: '旅游研学',
    title: '川藏线318国道自驾垂直自然带考察路线',
    prompt: '规划从成都至拉萨的川藏线自驾研学路线，梳理沿途垂直地带性变化、地质灾害防范及藏族风情考查点。',
    geoType: '旅游地理与自驾研学路线',
    geoRegion: '中国地理',
    perspective: '人文历史视角',
    usageCount: '37.9k'
  },
  {
    id: 'dili-6',
    tag: '区域生态',
    title: '塔里木盆地荒漠化治理与绿洲农业区位分析',
    prompt: '剖析南疆塔里木盆地干旱气候成因、高山冰雪融水补给特征、坎儿井/滴灌绿洲农业及荒漠化防治措施。',
    geoType: '高考地理考点与综合题拆解',
    geoRegion: '中国地理',
    perspective: '高考教研视角',
    usageCount: '52.6k'
  }
]);

function applyTemplate(item: ShowcaseItem) {
  emit('apply-template', {
    prompt: item.prompt,
    geoType: item.geoType,
    geoRegion: item.geoRegion,
    perspective: item.perspective
  });
}
</script>

<style scoped>
.nomads-showcase-section {
  margin-top: 2rem;
  width: 100%;
}

.showcase-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  margin-bottom: 1.25rem;
  padding-bottom: 0.75rem;
  border-bottom: 1px solid var(--card-border);
}

.showcase-title {
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--text-primary);
  background: var(--primary-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.showcase-subtitle {
  font-size: 0.825rem;
  color: var(--text-secondary);
  margin-top: 0.25rem;
}

.showcase-badge {
  font-size: 0.75rem;
  color: #a5b4fc;
  background: rgba(99, 102, 241, 0.12);
  border: 1px solid rgba(99, 102, 241, 0.25);
  padding: 4px 10px;
  border-radius: 20px;
}

.showcase-grid {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 1.25rem;
}

@media (min-width: 640px) {
  .showcase-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .showcase-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

.showcase-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  padding: 1.25rem;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid var(--card-border);
  border-radius: 14px;
  transition: all 0.25s ease;
}

.showcase-card:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(99, 102, 241, 0.4);
  transform: translateY(-3px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.75rem;
}

.scenario-tag {
  font-size: 0.75rem;
  font-weight: 600;
  padding: 3px 8px;
  border-radius: 6px;
  background: rgba(168, 85, 247, 0.15);
  color: #c084fc;
  border: 1px solid rgba(168, 85, 247, 0.3);
}

.usage-count {
  font-size: 0.75rem;
  color: var(--text-secondary);
}

.card-content {
  margin-bottom: 1rem;
  flex: 1;
}

.item-title {
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.4rem;
}

.item-prompt {
  font-size: 0.825rem;
  color: var(--text-secondary);
  line-height: 1.45;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  font-style: italic;
}

.card-action {
  padding-top: 0.75rem;
  border-top: 1px solid rgba(255, 255, 255, 0.04);
}

.apply-btn {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  padding: 0.5rem 1rem;
  background: rgba(99, 102, 241, 0.1);
  border: 1px solid rgba(99, 102, 241, 0.3);
  border-radius: 8px;
  color: #a5b4fc;
  font-size: 0.825rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
}

.showcase-card:hover .apply-btn {
  background: var(--primary-gradient);
  border-color: transparent;
  color: white;
}

.arrow-icon {
  width: 14px;
  height: 14px;
  transition: transform 0.2s ease;
}

.apply-btn:hover .arrow-icon {
  transform: translateX(3px);
}
</style>
