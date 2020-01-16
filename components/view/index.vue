<template>
    <view>
        <view class="uni-padding-wrap uni-common-mt">
            <button type="primary" @click="$emit('btnClick')" :size="size" open-type="getUserInfo">页面主操作 Normal</button>
            <button type="primary" loading="true">页面主操作 Loading</button>
            <button type="primary" disabled="true">页面主操作 Disabled</button>
            <button type="default">页面次要操作 Normal</button>
            <button type="default" disabled="true">页面次要操作 Disabled</button>
            <button type="warn">警告类操作 Normal</button>
            <button type="warn" disabled="true">警告类操作 Disabled</button>
            <view class="button-sp-area">
                <button type="primary" plain="true">按钮</button>
                <button type="primary" disabled="true" plain="true">不可点击的按钮</button>
                <button type="default" plain="true">按钮</button>
                <button type="default" disabled="true" plain="true">按钮</button>
                <button class="mini-btn" type="primary" size="mini">按钮</button>
                <button class="mini-btn" type="default" size="mini">按钮</button>
                <button class="mini-btn" type="warn" size="mini">按钮</button>
            </view>
        </view>
		
		<view class="uni-padding-wrap uni-common-mt">
			<view class="uni-title uni-common-mt">默认样式</view>
				<view>
					<checkbox-group>
						<label>
							<checkbox value="cb" checked="true" />选中
						</label>
						<label>
							<checkbox value="cb" />未选中
						</label>
					</checkbox-group>
				</view>
				<view class="uni-title uni-common-mt">不同颜色和尺寸的checkbox</view>
				<view>
					<checkbox-group>
						<label>
							<checkbox value="cb" checked="true" color="#FFCC33" style="transform:scale(0.7)" />选中
						</label>
						<label>
							<checkbox value="cb" color="#FFCC33" style="transform:scale(0.7)" />未选中
						</label>
					</checkbox-group>
				</view>
			</view>

			<view class="uni-padding-wrap">
				<view class="uni-title uni-common-mt">
					推荐展示样式
					<text>\n使用 uni-list 布局</text>
				</view>
			</view>
			<view class="uni-list">
				<checkbox-group @change="checkboxChange">
					<label class="uni-list-cell uni-list-cell-pd" v-for="item in items" :key="item.value">
						<view>
							<checkbox :value="item.value" :checked="item.checked" />
						</view>
						<view>{{item.name}}</view>
					</label>
				</checkbox-group>
			</view>
			
			
			<view class="uni-padding-wrap uni-common-mt">
				<view class="uni-title">默认样式</view>
				<view>
					<switch checked @change="switch1Change" />
					<switch @change="switch2Change" />
				</view>
				<view class="uni-title">推荐展示样式</view>
			</view>
			<view class="uni-list">
				<view class="uni-list-cell uni-list-cell-pd">
					<view class="uni-list-cell-db">开启中</view>
					<switch checked />
				</view>
				<view class="uni-list-cell uni-list-cell-pd">
					<view class="uni-list-cell-db">关闭</view>
					<switch />
				</view>
			</view>

	
		
		</view>
    </view>
</template>

<script>
export default {
	name: 'viewDemo',
	props: {
		size: {
			type: String,
			default: 'default'
		}
	},
	data() {
		return {
			background: ['color1', 'color2', 'color3'],
			indicatorDots: true,
			autoplay: true,
			interval: 2000,
			duration: 500,
			
			title: 'checkbox 复选框',
			items: [{
					value: 'USA',
					name: '美国'
				},
				{
					value: 'CHN',
					name: '中国',
					checked: 'true'
				},
				{
					value: 'BRA',
					name: '巴西'
				},
				{
					value: 'JPN',
					name: '日本'
				},
				{
					value: 'ENG',
					name: '英国'
				},
				{
					value: 'FRA',
					name: '法国'
				}
			],
			
			
			placeholder: '开始输入...'
		}
	},
	methods: {
		getUserInfo(){
			console.log(222);
		},
		changeIndicatorDots(e) {
			this.indicatorDots = !this.indicatorDots
		},
		changeAutoplay(e) {
			this.autoplay = !this.autoplay
		},
		intervalChange(e) {
			this.interval = e.target.value
		},
		durationChange(e) {
			this.duration = e.target.value
		},
		
		checkboxChange: function (e) {
			var items = this.items,
				values = e.detail.value;console.log(values);
			for (var i = 0, lenI = items.length; i < lenI; ++i) {
				const item = items[i]
				if(values.includes(item.value)){
					this.$set(item,'checked',true)
				}else{
					this.$set(item,'checked',false)
				}
			}
		},
		
		switch1Change: function (e) {
			console.log('switch1 发生 change 事件，携带值为', e.target.value)
		},
		switch2Change: function (e) {
			console.log('switch2 发生 change 事件，携带值为', e.target.value)
		}
	}
};
</script>

<style>
	.uni-list-cell {
	    justify-content: flex-start
	}
</style>
