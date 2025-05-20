<script setup lang="ts">
</script>

<template>
  <main>
    <TileContainer>
      <Tile 
        title="文档" 
        size="medium" 
        color="#0078D7" 
        :icon="IconDocumentation"
        route="/documentation"
        @click="navigateTo"
      />
      <Tile 
        title="社区" 
        size="small" 
        color="#107C10" 
        :icon="IconCommunity"
        route="/community"
        @click="navigateTo"
      />
      <Tile 
        title="生态系统" 
        size="large" 
        color="#D83B01" 
        :icon="IconEcosystem"
        isLive
        route="/ecosystem"
        @click="navigateTo"
      >
        <div class="live-content">
          <p>最新动态</p>
          <p>查看Vue生态系统的最新更新</p>
        </div>
      </Tile>
      <Tile 
        title="支持" 
        size="medium" 
        color="#5C2D91" 
        :icon="IconSupport"
        route="/support"
        @click="navigateTo"
      />
      <Tile 
        title="工具" 
        size="small" 
        color="#FFB900" 
        :icon="IconTooling"
        route="/tools"
        @click="navigateTo"
      />
      <Tile 
        title="关于" 
        size="medium" 
        color="#E74856" 
        route="/about"
        @click="navigateTo"
      />
    </TileContainer>
  </main>
</template>

<script setup lang="ts">
import { useRouter } from 'vue-router';
import TileContainer from '@/components/TileContainer.vue';
import Tile from '@/components/Tile.vue';
import IconDocumentation from '@/components/icons/IconDocumentation.vue';
import IconCommunity from '@/components/icons/IconCommunity.vue';
import IconEcosystem from '@/components/icons/IconEcosystem.vue';
import IconSupport from '@/components/icons/IconSupport.vue';
import IconTooling from '@/components/icons/IconTooling.vue';

const router = useRouter();

const navigateTo = (route: string) => {
  if (route) {
    router.push(route);
  }
};
</script>

<style scoped>
.live-content {
  font-size: 0.9rem;
  line-height: 1.2;
}
</style>
