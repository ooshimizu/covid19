<template>
  <div>
    <card-row class="DataBlock">
      <!-- 陽性者の属性 -->
      <confirmed-cases-attributes-card />
      <!-- 陽性者数（区市町村別） -->
      <confirmed-cases-by-municipalities-card />
      <!-- 発症日別による陽性者数の推移 -->
      <positive-number-by-developed-date-card />
      <!-- 確定日別による陽性者数の推移 -->
      <positive-number-by-diagnosed-date-card />
      <!-- 検査実施件数 -->
      <tested-number-card />
    </card-row>
    <card-row class="DataBlock">
      <!-- 受診相談窓口における相談件数 -->
      <monitoring-consultation-desk-reports-number-card />
      <!-- 新型コロナコールセンター相談件数 -->
      <telephone-advisory-reports-number-card />
    </card-row>
    <card-row class="DataBlock">
      <!-- 都営地下鉄の利用者数の推移 -->
      <metro-card />
      <!-- 都庁来庁者数の推移 -->
      <agency-card />
    </card-row>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import CardRow from '@/components/cards/CardRow.vue'

// NOTE: 以下，ブラウザでの表示順に合わせて component を import する
// 陽性者の属性
import ConfirmedCasesAttributesCard from '@/components/cards/ConfirmedCasesAttributesCard.vue'
// 陽性者数（区市町村別）
import ConfirmedCasesByMunicipalitiesCard from '@/components/cards/ConfirmedCasesByMunicipalitiesCard.vue'
// 発症日別による陽性者数の推移
import PositiveNumberByDevelopedDateCard from '@/components/cards/PositiveNumberByDevelopedDateCard.vue'
// 確定日別による陽性者数の推移
import PositiveNumberByDiagnosedDateCard from '@/components/cards/PositiveNumberByDiagnosedDateCard.vue'
// 検査実施件数
import TestedNumberCard from '@/components/cards/TestedNumberCard.vue'
// 受診相談窓口における相談件数
import MonitoringConsultationDeskReportsNumberCard from '@/components/cards/MonitoringConsultationDeskReportsNumberCard.vue'
// 新型コロナコールセンター相談件数
import TelephoneAdvisoryReportsNumberCard from '@/components/cards/TelephoneAdvisoryReportsNumberCard.vue'
// 都営地下鉄の利用者数の推移
import MetroCard from '@/components/cards/MetroCard.vue'
// 都庁来庁者数の推移
import AgencyCard from '@/components/cards/AgencyCard.vue'

export default Vue.extend({
  components: {
    CardRow,
    ConfirmedCasesAttributesCard,
    ConfirmedCasesByMunicipalitiesCard,
    PositiveNumberByDevelopedDateCard,
    PositiveNumberByDiagnosedDateCard,
    TestedNumberCard,
    MonitoringConsultationDeskReportsNumberCard,
    TelephoneAdvisoryReportsNumberCard,
    MetroCard,
    AgencyCard,
  },
})
</script>

<style lang="scss" scoped>
.DataBlock {
  margin: 20px -8px;

  .DataCard {
    @include largerThan($medium) {
      padding: 10px;
    }

    @include lessThan($small) {
      padding: 4px 8px;
    }
  }
}
</style>
