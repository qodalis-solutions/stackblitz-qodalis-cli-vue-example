<script setup lang="ts">
import { Cli, CliConfigProvider, CliPanel } from '@qodalis/vue-cli';
import '@qodalis/cli/assets/cli-panel.css';
import { guidModule } from '@qodalis/cli-guid';
import { filesModule } from '@qodalis/cli-files';
import { usersModule } from '@qodalis/cli-users';
import type { CliOptions, ICliModule } from '@qodalis/cli-core';

const modules: ICliModule[] = [
    guidModule,
    filesModule,
    usersModule,
];

const options: CliOptions = {};
</script>

<template>
  <CliConfigProvider :modules="modules" :options="options">
    <div class="window">
      <div class="titlebar">
        <span class="dot red"></span>
        <span class="dot yellow"></span>
        <span class="dot green"></span>
        <span class="title">qodalis-cli</span>
      </div>
      <div class="body">
        <Cli :style="{ width: '100%', height: '100%' }" />
      </div>
    </div>
    <CliPanel :options="{ position: 'right', isHidden: true }" />
  </CliConfigProvider>
</template>

<style scoped>
.window {
  display: flex;
  flex-direction: column;
  height: 100vh;
  padding: 24px;
  box-sizing: border-box;
}

.titlebar {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 12px 16px;
  background: #1c1f2b;
  border-bottom: 1px solid #2a2f3a;
  border-radius: 10px 10px 0 0;
  flex-shrink: 0;
}

.dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
}

.dot.red { background: #ff5f57; }
.dot.yellow { background: #febc2e; }
.dot.green { background: #28c840; }

.title {
  margin-left: 8px;
  font-family: 'SF Mono', 'Fira Code', 'Cascadia Code', monospace;
  font-size: 13px;
  color: rgba(255, 255, 255, 0.45);
}

.body {
  flex: 1;
  min-height: 0;
  background: #000;
  border-radius: 0 0 10px 10px;
  overflow: hidden;
  border: 1px solid #2a2f3a;
  border-top: none;
}
</style>
