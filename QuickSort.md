```python
class QuickSort:
    #选择一个第一个值作为标准，大于它的放到右边，小于它的放到左边，然后对左右部分递归调用快速排序
    def quickSort(self, arr, left, right):
         if left < right:
            pivot = self.partition(arr,left,right)
            self.quickSort(arr,left,pivot-1)
            self.quickSort(arr,pivot+1,right)

    def partition(self, arr, left, right):
        key = arr[left]
        while left < right :
            while left<right and arr[right]>=key:
                right -= 1
            arr[left] = arr[right]
            while left<right and arr[left]<=key:
                left += 1
            arr[right] = arr[left]
        arr[left] = key
        return left

arr = [65,58,95,10,57,62,13,106,78,23,85]
a = QuickSort()
a.quickSort(arr,0,len(arr)-1);
print(arr)
```
