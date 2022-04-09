<!-- Log Viewer component test -->
<template>
  <!-- the v-html xlates raw html -->
  <log-viewer
    v-bind:object_name="test_object_name"
    v-bind:logs="logs"></log-viewer>
  <button @click="startTest">Start Test</button>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import { LogViewer } from "@egadams/vue3-plugin";
import { LogObjectProcessorTest /* @vite-ignore */ } from 'log-object-processor';
export default defineComponent({
    name: "LogViewerTest",
    components: {
        LogViewer
    },
    data() {
        return {
            test_object_name: "tester",
            processor_test: new LogObjectProcessorTest(),
            logs: [{
                    id: "1",
                    timestamp: 100,
                    message: "test message 1",
                    method: "test",
            }, {
                    id: "2",
                    timestamp: 100,
                    message: "test message 2",
                    method: "test",
            }],
        };
    },
    methods: {
        startTest() {
            this.processor_test.testMe();
            this.logs = this.processor_test.writtenLogs;
        },
    },
});
</script>

<style scoped></style>
