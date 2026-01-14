<template>
  <section
    v-if="devices && devices.length > 0"
    class="col-span-3 bg-white rounded-lg shadow p-6 overflow-auto max-h-[calc(100vh-128px)]"
  >
    <h2 class="text-lg font-semibold mb-4">Monitoramento do Dispositivo: {{ selectedDeviceId }}</h2>

    <div v-for="device in devices" :key="device.raspberry_id">
      <DeviceStatusGrid 
        v-show="device.raspberry_id === selectedDeviceId"
        :device-details="device" 
      />
    </div>
  </section>
</template>

<script>
import DeviceStatusGrid from './DeviceStatusGrid.vue';

export default {
  name: 'DeviceDetails',
  components: {
    DeviceStatusGrid
  },
  props: {
    devices: {
      type: Array,
      default: () => []
    },
    selectedDeviceId: {
      type: [String, Number],
      default: null
    },
    loading: {
      type: Boolean,
      default: false
    }
  }
};
</script>

