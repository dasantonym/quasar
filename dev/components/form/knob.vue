<template>
  <div>
    <div class="layout-padding">
      <div class="label bg-secondary text-white">
        Model <span class="right-detail"><em>{{ model }}</em></span>
      </div>

      <p class="caption">Default</p>
      <q-knob
        v-model="model"
        :min="min"
        :max="max"
        @change="onChange"
        @input="onInput"
      />
      <q-knob
        class="text-primary"
        :value="model"
        :min="min"
        :max="max"
        @change="val => { model = val; onChange(val) }"
        @input="onInput"
      />

      <p class="caption">With Step ({{ min }} to {{ max }}, step 10)</p>
      <q-knob
        v-model="model"
        :min="min"
        :max="max"
        :step="10"
      />

      <p class="caption">With Step ({{ min }} to {{ maxSmall }}, step 0.01) - decimals set to 1</p>
      <q-knob
        v-model="modelSmall"
        :min="min"
        :max="maxSmall"
        :step="0.01"
        :decimals="1"
      />

      <p class="caption">With Step ({{ min }} to {{ maxSmall }}, step 0.01) - decimals not set (auto 2)</p>
      <q-knob
        v-model="modelSmall"
        :min="min"
        :max="maxSmall"
        :step="0.01"
      />

      <p class="caption">Styling</p>
      <div class="group">
        <q-knob
          v-model="model"
          size="150px"
          color="red"
          line-width="2px"
          track-color="white"
          :min="min"
          :max="max"
        >
          $ {{ model }}
        </q-knob>

        <q-knob
          v-model="model"
          style="font-size: 3rem"
          color="amber-7"
          :min="min"
          :max="max"
          :step="5"
        />

        <q-knob
          v-model="model"
          size="120px"
          style="font-size: 1.5rem"
          color="secondary"
          track-color="yellow-3"
          line-width="5px"
          :min="min"
          :max="max"
          :step="5"
        >
          <q-icon class="on-left" name="euro_symbol" /> {{ model }}
        </q-knob>
      </div>

      <p class="caption">Readonly state</p>
      <q-knob
        v-model="model"
        :min="min"
        :max="max"
        color="primary"
        readonly
      >
        <q-icon class="on-left" name="volume_up" /> {{ model }}
      </q-knob>

      <p class="caption">Disabled state</p>
      <q-knob
        v-model="model"
        :min="min"
        :max="max"
        disable
      >
        <q-icon class="on-left" name="volume_up" /> {{ model }}
      </q-knob>

      <p class="caption">Inside Field</p>
      <q-field
        label="Knob"
        helper="Touch to change"
        icon="cake"
      >
        <q-knob
          v-model="model"
          :min="min"
          :max="max"
        >
          <q-icon class="on-left" name="volume_up" /> {{ model }}
        </q-knob>
      </q-field>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      model: 30,
      modelSmall: 1.1,
      min: 0,
      max: 50,
      maxSmall: 2
    }
  },
  watch: {
    model (val, old) {
      console.log(`Changed from ${JSON.stringify(old)} to ${JSON.stringify(val)}`)
    }
  },
  methods: {
    onChange (val) {
      console.log('@change', JSON.stringify(val))
    },
    onInput (val) {
      console.log('@input', JSON.stringify(val))
    }
  }
}
</script>
