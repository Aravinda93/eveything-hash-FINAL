<template>
  <div>
    <h1>Testing Pre-Hash for Event Hash</h1>
  </div>
</template>

<script>
import Vue from 'vue'
import {objectToEvent, ObjectEvent, AggregationEvent} from 'epcis2.js'

export default Vue.extend({
  mounted() {
    const object = {
                      type: 'ObjectEvent',
                      eventTime: '2005-04-03T20:33:31.116-06:00',
                      eventTimeZoneOffset: '-06:00',
                      epcList: ['urn:epc:id:sgtin:0614141.107346.2017'],
                      action: 'OBSERVE',
                      bizStep: 'shipping',
                      readPoint: {
                        id: 'urn:epc:id:sgln:0614141.07346.1234',
                      }
                    };
    
    const event = objectToEvent(object);
    console.log(event instanceof ObjectEvent)       // true
    console.log(event instanceof AggregationEvent)  // false
    console.log(event.toString());
    console.log("MOUNTED : " + JSON.stringify(event, null, 4))
  },
  created() {
    console.log("CREATED")
  }
})
</script>