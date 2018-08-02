<script>
import rateData from '@/components/homePage/dataConfig'
export default {
    name: 'homePage',
    data() {
        return {
            rateData,
            clickList: ['basic'],
            nowRate: 0,
            nowDetail: {},
        }
    },
    computed: {
        nowImg() {
            if (this.isCategory('manager')) {
                this.nowRate = 3
                return require('@/assets/img-ship-master.png')
            } else if (this.isCategory('js')) {
                this.nowRate = 2
                return require('@/assets/img-ship-developer.png')
            } else if (this.isCategory('css')) {
                this.nowRate = 1
                return require('@/assets/img-ship-beginner.png')
            } else {
                this.nowRate = 0
                return require('@/assets/img-ship-noob.png')
            }
        },
    },
    methods: {
        isCategory(category) {
            return this.clickList.findIndex(e => e == category) != -1
        },
        renderData(category) {
            return this.rateData.filter(e => e.category == category)
        },
        showDetail(data) {
            this.nowDetail = data
        },
        nowLength(data) {
            return data.filter(e => e.checked == true).length
        },
        update(id, index, val) {
            let goalData = this.rateData.find(e => e.id == id)
            if (val == 'recommend') {
                goalData.recommend[index].checked = true
                goalData.done = goalData.recommend.every(e => e.checked == true)
            } else if (val == 'optional') {
                goalData.optional[index].checked = true
            }

            if (this.renderData('basic').every(e => e.done == true) && !this.clickList.includes('css')) {
                this.clickList.push('css')
            }
            if (this.renderData('css').every(e => e.done == true) && !this.clickList.includes('js')) {
                this.clickList.push('js')
            }
            if (this.renderData('js').every(e => e.done == true) && !this.clickList.includes('manager')) {
                this.clickList.push('manager')
            }
        }
    },
    created() {
        this.nowDetail = rateData[0]
    }
}
</script>

<template src="./template.html"></template>
<style lang="scss" src="./style.scss"></style>
