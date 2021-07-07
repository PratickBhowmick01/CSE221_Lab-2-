# CSE221_Lab-2

#Task01
#Best case- when the array is already sorted.

p = open('input1.txt', "r")
q = open('output1.txt', "w")

array = p.read().split("\n") 
array = list(map(int, array[1].split(" "))) 

def bubbleSort(arr):
    count = 0 
    for i in range(len(arr)-1):
        
        if(count == len(arr)-i):  #if no swapping takes place in inner loop
            break               #then array is sorted
        else:
            count = 0 
        for j in range(len(arr)-i-1): 
            
            if arr[j] > arr[j+1]:
                arr[j+1], arr[j] = arr[j], arr[j+1]
            else:    
                count += 1          #counts no. of no swapping   
 
bubbleSort(array) 
for i in array:
    q.write(str(i) + " ")    

p.close()  
q.close() 


#Task-02
f = open("input2.txt", "r")
p = open("output2.txt", "w")

input1 = f.readline()
input1 = input1.split(" ")
num1 = int(input1[1])  
array1 = f.readline()
array1 = list(map(int, array1.split(" "))) 

input2 = f.readline()
input2 = input2.split(" ")
num2 = int(input2[1])  
array2 = f.readline()
array2 = list(map(int, array2.split(" "))) 

def min_selection_sort(a):
    for i in range(len(a)-1):
        min_v = a[i]         
        min_idx = i              
        
        for j in range(i+1,len(a)):
            if(a[j] < min_v):   
                min_v = a[j]       
                min_idx = j                  

        a[i],a[min_idx] = min_v,a[i]  
        
min_selection_sort(array1)
min_selection_sort(array2)

for i in range(0, num1):
    p.write(str(array1[i]))
    p.write(" ")
p.write("\n")
for i in range(0, num2):
    p.write(str(array2[i]))
    p.write(" ")
 
f.close() 
p.close() 


#Task-03
f = open("input3.txt", "r")
fp = open("output3.txt", "w")

input1 = int(f.readline()) 
id_1 = f.readline()
id_1 = list(map(int, id_1.split(" ")))  
marks_1 = f.readline()
marks_1 = list(map(int, marks_1.split(" ")))

input2 = int(f.readline()) 
id_2 = f.readline()
id_2 = list(map(int, id_2.split(" ")))  
marks_2 = f.readline()
marks_2 = list(map(int, marks_2.split(" ")))

def insertionSort(a,b):
    for i in range(1, len(a)):
        value1 = a[i]
        value2 = b[i] 
        j = i-1
        while(j >= 0):
            if (value1 > a[j]):
                a[j+1],a[j] = a[j],value1
                b[j+1], b[j] = b[j],value2
                j -= 1
            else:
                break 

insertionSort(marks_1, id_1)
insertionSort(marks_2, id_2) 

for i in id_1:
    fp.write(str(i)) 
    fp.write(" ") 
fp.write("\n")
for i in id_2:
    fp.write(str(i)) 
    fp.write(" ") 

f.close() 
fp.close() 


#Task-04
f = open("input4.txt", "r")
fp = open("output4.txt", "w")

num1 = int(f.readline()) 
array1 = f.readline()
array1 = list(map(int, array1.split(" "))) 

num2 = int(f.readline()) 
array2 = f.readline()
array2 = list(map(int, array2.split(" ")))  

def merge(A,l,mid,h):
    i,k = l,l
    j = mid+1
    B = [0]*len(A) 
    
    while(i <= mid and j <= h):
        if(A[i] <= A[j]):
            B[k] = A[i]
            i += 1
        else:
            B[k] = A[j]
            j += 1
        k += 1
    
    if(i > mid):
        while(j <= h):
            B[k] = A[j]
            j += 1
            k += 1    
    else:
        while(i <= mid):
            B[k] = A[i]
            i += 1
            k += 1
    
    for k in range(l,h+1):
        A[k] = B[k]

def mergeSort(A,l,h):
    if (l < h):
        mid = (l+h) // 2
        mergeSort(A,l,mid)
        mergeSort(A,mid+1, h)
        merge(A,l,mid,h) 

mergeSort(array1,0,num1-1)  
mergeSort(array2,0,num2-1)

for i in range(0, num1):
    fp.write(str(array1[i]))
    fp.write(" ")
fp.write("\n")
for i in range(0, num2):
    fp.write(str(array2[i]))
    fp.write(" ")

f.close() 
fp.close()












