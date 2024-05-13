一种简单直观的排序算法。

![[Pasted image 20240513033257.png]]

方法思路：
- 1. 初始状态下，未排序部分为整个数组。
- 2. 在未排序部分找到最小（或最大）的元素，将其与未排序部分的第一个元素交换位置。
- 3. 将未排序部分的范围缩小一个元素，即从第二个元素到最后一个元素。
- 4. 重复上述步骤，直到未排序部分为空。

时间复杂度：O($N^2$)

**优点**：
  - **简单易懂**：实现方便，理解容易。
  - **不依赖于数据**：无论数据如何，比较次数都是固定的。
  - **原地排序**：不需要额外的存储空间。

**缺点**：
  - **效率低下**：即使数据已经排序，时间复杂度依然为O($N^2$)。
  - **不稳定排序**：选择排序可能会改变相等元素的原始顺序。
  - **性能不佳**：通常比其他O($N^2$)排序算法（如插入排序）性能差。

**代码实现**
```java
public static void select_sort(int array[],int lenth){

   for(int i=0;i<lenth-1;i++){

       int minIndex = i;
       for(int j=i+1;j<lenth;j++){
          if(array[j]<array[minIndex]){
              minIndex = j;
          }
       }
       if(minIndex != i){
           int temp = array[i];
           array[i] = array[minIndex];
           array[minIndex] = temp;
       }
   }
}
```