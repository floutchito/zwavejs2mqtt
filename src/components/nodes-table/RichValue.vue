<template>
	<div :title="value.description">
		<span
			v-if="value !== undefined && value.icon === ''"
			:style="'padding-top: 4px; ' + value.displayStyle"
			>{{ value.displayValue }}</span
		>
		<v-layout
			v-if="value !== undefined && value.icon !== ''"
			:label="value.description"
			:justify-start="value.align === 'left'"
			:justify-center="value.align === 'center'"
			:justify-end="value.align === 'right'"
		>
			<svg-icon
				type="mdi"
				:path="value.icon"
				:style="value.iconStyle"
			></svg-icon>
			<span
				v-if="value !== undefined && !!value.displayValue"
				:style="'padding-top: 4px; ' + value.displayStyle"
				>{{ value.displayValue }}</span
			>
		</v-layout>
	</div>
</template>

<script>
import SvgIcon from '@jamescoyle/vue-icon'
export default {
	props: {
		value: {
			type: Object,
			required: true,
			default: () => {
				return {
					align: 'left',
					icon: '',
					iconStyle: '',
					displayValue: '',
					displayStyle: '',
					description: '',
					rawValue: undefined,
				}
			},
		},
	},
	components: {
		SvgIcon,
	},
}
</script>
