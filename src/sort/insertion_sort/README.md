##### 插入排序

类似打牌时排列牌的顺序，假设前面的都是已经排好序的，只要找出当前牌要插入的位置即可。

```javascript
// 从小到大排列
export default function sort(nums: Array<number>) {
  if (nums === null || nums === undefined) {
    return
  }

  for (let j = 1, length = nums.length; j < length ;j++ ) { // 处理[0]牌时，手里还没有牌，所以它就是已经排好序的，直接放入手中即可。所以我们从[1]牌开始
    let key = nums[j]
    let i = j -1
    while(i>=0) {
      if (nums[i] <= key) { //假定前面的牌都是排好序的，所以如果要插入的牌[j]比前面的牌[i]大，那就不需要查找位置了，[j]的位置就是j，是准确的，跳出这次循环
        break
      }
      // 否则表示[i+1]的位置不对，要给它找出正确的位置
      nums[i+1] = nums[i] //因为从小到大排列，所以[i]处的值要往后移动一次
      i = i-1 // 然后i往前退一位，继续跟要插入的值比较大小
      console.log('交换值:', nums.join(','))
    }
    nums[i + 1] = key // 跳出循环之后，key就是要插入的值，[i]就是比key刚好小的那个值，所以i+1就是key的位置，给这个位置赋值即可
    console.log('当前值：', nums.join('_'))
  }
}
```