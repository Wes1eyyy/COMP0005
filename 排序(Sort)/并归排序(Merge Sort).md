一种使用分治策略的排序算法。

![[Pasted image 20240513033409.png]]

方法思路：
- 1. 将待排序数组分成两个子数组。
- 2. 递归地对两个子数组进行归并排序。
- 3. 合并两个已排序的子数组以得到最终的排序结果。

时间复杂度：O($Nlog_N$)

归并排序的时间复杂度分析：
- 将数组分成两个子数组的过程需要O(l$og N$)次操作（每次对半分）。
- 合并两个子数组的过程需要O(N)次操作（每次比较和合并）。
- 因此，总的时间复杂度是O($N log_N$)。

**优点**：
  - **高效稳定**：时间复杂度始终为O($N log_N$)，对于大数据集非常有效。
  - **稳定排序**：保持等值的元素顺序。
  - **适用于外部排序**：适合于大数据集，可以很容易地被应用于外部存储排序。

**缺点**：
  - **空间消耗高**：需要与原始数据等量的额外空间进行数组元素的合并。
  - **非原地排序**：归并排序需要额外的内存空间，对于内存敏感的应用可能不是最佳选择。

**代码实现**
```java
public static void merge_sort(int a[],int first,int last,int temp[]){

  if(first < last){
      int middle = (first + last)/2;
      merge_sort(a,first,middle,temp);//左半部分排好序
      merge_sort(a,middle+1,last,temp);//右半部分排好序
      mergeArray(a,first,middle,last,temp); //合并左右部分
  }
}
```

```java
//合并 ：将两个序列a[first-middle],a[middle+1-end]合并
public static void mergeArray(int a[],int first,int middle,int end,int temp[]){     
  int i = first;
  int m = middle;
  int j = middle+1;
  int n = end;
  int k = 0; 
  while(i<=m && j<=n){
      if(a[i] <= a[j]){
          temp[k] = a[i];
          k++;
          i++;
      }else{
          temp[k] = a[j];
          k++;
          j++;
      }
  }     
  while(i<=m){
      temp[k] = a[i];
      k++;
      i++;
  }     
  while(j<=n){
      temp[k] = a[j];
      k++;
      j++; 
  }

  for(int ii=0;ii<k;ii++){
      a[first + ii] = temp[ii];
  }
}
```