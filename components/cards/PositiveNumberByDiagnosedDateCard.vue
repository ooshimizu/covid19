<template>
  <v-col cols="12" md="6" class="DataCard">
    <client-only>
      <time-bar-chart
        :title="$t('確定日別による陽性者数の推移')"
        :title-id="'positive-number-by-diagnosed-date'"
        :chart-id="'positive-number-by-diagnosed-date'"
        :chart-data="graphData"
        :date="date"
        :unit="$t('人')"
      >
        <template v-slot:additionalDescription>
          <span>{{ $t('（注）') }}</span>
          <ul>
            <li>
              {{
                $t(
                  '各保健所から報告があった患者の発生情報を、検査により陽性であることを医師が確認した日別（確定日別）に整理したものである'
                )
              }}
            </li>
          </ul>
        </template>
      </time-bar-chart>
    </client-only>
  </v-col>
</template>

<script>
import Data from '@/data/positive_by_diagnosed.json'
import formatGraph from '@/utils/formatGraph'
import TimeBarChart from '@/components/TimeBarChart.vue'
import { calcDayBeforeRatio } from '@/utils/formatDayBeforeRatio'

export default {
  components: {
    TimeBarChart: {
      extends: TimeBarChart,
      computed: {
        displayInfo() {
          const { lastDay, lastDayData } = calcDayBeforeRatio({
            displayData: this.displayData,
            dataIndex: 1,
          })
          if (this.dataKind === 'transition') {
            return {
              lText: lastDayData,
              sText: `${lastDay} ${this.$t('日別値')}（${this.$t(
                '現在判明している人数であり、後日修正される場合がある'
              )}）`,
              unit: this.unit,
            }
          }
          return {
            lText: lastDayData,
            sText: `${lastDay} ${this.$t('累計値')}`,
            unit: this.unit,
          }
        },
      },
    },
  },
  data() {
    const formatData = Data.data.map((data) => {
      return {
        日付: data.diagnosed_date,
        小計: data.count,
      }
    })

    // 陽性患者数グラフ
    const graphData = formatGraph(formatData)

    const { date } = Data

    return {
      date,
      graphData,
    }
  },
}
</script>
