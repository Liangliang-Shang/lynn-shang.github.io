Title: Algorithm  
Date: 2016-02-17 21:54  
Category: Alogrithm   
Tags: Python, Algorithm  
Slug: algorithm  
Author: lshang  
Summary: Algorithm implemented in Python  

## Averaged Randomise
We could call it RedPacket/RedEnvelope Algorithm, assigning a list averagedly with a limited total
```python
import random

def averagedRandomise(Num, Total, style=0.5):
    Total   = Total * 1.0
    UNIT    = 0.01
    packets = list()

    if(Num < 1 or Total < UNIT or Total / Num < UNIT): 
        print("Error! Can't averaged randomise %d - %f" % (Num, Total))
        return

    if(Num == 1):
        packets.append(Total)
        return packets

    summary     = 0.0
    avg         = round((Total / Num), 2)
    # Keep the last one, making it be equal to Total - summary
    total       = Total - avg
    num         = Num - 1

    # Randomise (Num - 1) values into packets
    for i in range(num):
        avg100      = round(((total - summary) / (num - i)), 2) * 100
        delta100    = avg100 / (num - i)
        value       = random.choice(range(int(avg100 - delta100)
                                                , int(avg100 + delta100)
                                                , int(UNIT * 100))) / 100.0
        summary     += value
        packets.append(value)
    else:
        # sum of (Num - 1) over Total!!! Re-do it with less style
        if(summary > Total):
            return averagedRandomise(Num, Total, 0.2)
        else: 
            # Append the last one into packets
            packets.append(round(Total - summary, 2))
            return packets
```

## Bubble Sort
Refer to [Wiki](https://en.wikipedia.org/wiki/Bubble_sort)
```python
def bubbleSort(dataList=None):
    length = len(dataList)

    if(length == 0 or length == 1):
        return dataList

    for i in range(length):
        swapped = False
        for j in range(length-i-1):
            print("i = %d, j = %d, %s" % (i, j, dataList)), 
            if(dataList[j] > dataList[j+1]):
                dataList[j+1], dataList[j] = dataList[j], dataList[j+1]
                swapped = True
            print("-> %s" % ( dataList))
        else: 
            if not swapped:
                    break;

    return dataList

if __name__ == "__main__":
    dataList = [5, 1, 4, 2, 8]
    bubbleSort(dataList[0:])
```
```Text
i = 0, j = 0, [5, 1, 4, 2, 8] -> [1, 5, 4, 2, 8]
i = 0, j = 1, [1, 5, 4, 2, 8] -> [1, 4, 5, 2, 8]
i = 0, j = 2, [1, 4, 5, 2, 8] -> [1, 4, 2, 5, 8]
i = 0, j = 3, [1, 4, 2, 5, 8] -> [1, 4, 2, 5, 8]
i = 1, j = 0, [1, 4, 2, 5, 8] -> [1, 4, 2, 5, 8]
i = 1, j = 1, [1, 4, 2, 5, 8] -> [1, 2, 4, 5, 8]
i = 1, j = 2, [1, 2, 4, 5, 8] -> [1, 2, 4, 5, 8]
i = 2, j = 0, [1, 2, 4, 5, 8] -> [1, 2, 4, 5, 8]
i = 2, j = 1, [1, 2, 4, 5, 8] -> [1, 2, 4, 5, 8]
```

## Insert Sort
Refer to [Wiki](https://en.wikipedia.org/wiki/Insertion_sort)  
```Python
def insertSort(dataList=None):
    length = len(dataList)
    
    if(length == 0 or length == 1): 
        return dataList

    for i in range(1, length):
        print "i =", i, dataList, 
        temp = dataList[i]
        for j in range(0, i): 
            if(dataList[j] > dataList[i]):
                for k in range(i, j, -1):
                    dataList[k] = dataList[k-1]
                dataList[j] = temp
                break;
        print "->", dataList

    return dataList

if __name__ == "__main__":
    dataList = [3, 7, 4, 9, 5, 2, 6, 1]
    insertSort(dataList[0:])
```
```Text
i = 1 [3, 7, 4, 9, 5, 2, 6, 1] -> [3, 7, 4, 9, 5, 2, 6, 1]
i = 2 [3, 7, 4, 9, 5, 2, 6, 1] -> [3, 4, 7, 9, 5, 2, 6, 1]
i = 3 [3, 4, 7, 9, 5, 2, 6, 1] -> [3, 4, 7, 9, 5, 2, 6, 1]
i = 4 [3, 4, 7, 9, 5, 2, 6, 1] -> [3, 4, 5, 7, 9, 2, 6, 1]
i = 5 [3, 4, 5, 7, 9, 2, 6, 1] -> [2, 3, 4, 5, 7, 9, 6, 1]
i = 6 [2, 3, 4, 5, 7, 9, 6, 1] -> [2, 3, 4, 5, 6, 7, 9, 1]
i = 7 [2, 3, 4, 5, 6, 7, 9, 1] -> [1, 2, 3, 4, 5, 6, 7, 9]
```
