<template>
  <div class="glass-card ticker-card">
    <div class="ticker-wrapper">
      <div v-for="(item, index) in tickerItems" :key="index" class="ticker-item">
        <span>{{ item.text }}</span>
        <span style="color: var(--success-color); font-weight: bold;">[解析生成完成]</span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const tickerItems = ref([
  { text: '用户 138****9281 完成了喀斯特地貌溶洞与峰林成因机制深度解析' },
  { text: '用户 177****4019 完成了青藏高原隆升对东亚季风气候影响的考点拆解' },
  { text: '用户 189****3320 生成了江南水乡聚落分布与古镇水运历史地理报告' },
  { text: '用户 131****8829 完成了西北荒漠化治理与绿洲农业区位分析' },
  { text: '用户 153****1290 完成了川藏线318自驾研学路线与沿线地质灾害考察指南' },
]);
</script>
