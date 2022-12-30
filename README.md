# dsq4import java.util.*;

public class a3q4 {

    static Scanner sc = new Scanner(System.in);

    public static void main(String[] args)

    {

        int ch;

        do

        {

            System.out.println("\n1.Insertion Sort");

            System.out.println("\n2.Selection Sort");

            System.out.println("\n3.Bubble Sort");

            System.out.println("\n4.Quick Sort");

            System.out.println("\n5.Merge Sort");

            System.out.println("\n6.Exit");

            System.out.println("Enter Your Choice:- ");

            ch = sc.nextInt();

            

            switch(ch)

            {

                case 1:

                    int arr[] = insertarr();

                    insertion(arr);

                    System.out.println(Arrays.toString(arr));

                    break;

                   

                case 2:

                    int arr2[] = insertarr();

                    selectionsort(arr2);

                    System.out.println(Arrays.toString(arr2));

                    break;

                    

                case 3:

                    int arr3[] = insertarr();

                    bubblesort(arr3);

                    System.out.println(Arrays.toString(arr3));

                    break;

                

                case 4:

                    int arr4[] = insertarr();

                    int high = arr4.length-1;

                    quicksort(arr4, 0 , high);

                    System.out.println(Arrays.toString(arr4));

                    break;

                    

                case 5:

                    int arr5[] = insertarr();

                    int sortedarr[] = mergesort(arr5);

                    System.out.println(Arrays.toString(sortedarr));

                    break;

            }

        }while(ch!= 6);

    }

    

    static int[] insertarr()

    {

        int size;

        System.out.println("Enter The Size Of An Array");

        size = sc.nextInt();

        int arr[]=new int[size];

        System.out.println("Enter The data To Store In Array");

        for(int i = 0;i<size;i++)

        {

            arr[i] = sc.nextInt();

        }

        return arr;

    }

    

    static void swap(int [] arr, int first,int second)

    {

        int temp = arr[first];

        arr[first] = arr[second];

        arr[second] = temp;

    }

    

    static int getmex(int [] arr,int start, int end)

    {

        int max = start;

        for(int i =0;i<=end;i++)

        { 

            if(arr[max] < arr[i])

            {

                max = i;

            }

        }

        return max;

    }

    

    static void insertion(int [] arr)

    {

        for(int i=0;i<arr.length-1;i++)

        {

            for(int j=i+1;j>0;j--)

            {

                if(arr[j]<arr[j-1])

                {

                    swap(arr,j,j-1);

                }

                else

                {

                    break;

                }

            }

        }

    }

    

    static void selectionsort(int [] arr)

    {

        for(int i =0;i<arr.length;i++)

        {

            int last = arr.length-i-1;

            int max = getmex(arr,0,last);

            swap(arr,max,last);

        }

    }

    

    static void bubblesort(int[] arr)

    {

        boolean swapped;

        for(int i=0;i<arr.length;i++)

        {

            swapped = false;

            for(int j=1;j<arr.length-i;j++)

            {

                if(arr[j]<arr[j-1])

                {

                    swap(arr,j,j-1);

                    swapped = true;

                }

            }

            if(!swapped) 

            {

                break;

            }

        }

    }

    

    static void quicksort(int [] arr, int low,int high)

    {

        if(low>=high)

        {

            return;

        }

        int s = low;

        int e = high;

        int m = s + (e-s)/2;

        int pivot = arr[m];

        

        while(s<=e)

        {

            while(arr[s]<pivot)

            {

                s++;

            }

            while(arr[e]>pivot)

            {

                e--;

            }

            if(s<=e)

            {

                swap(arr,s,e);

                s++;

                e--;

            }

        }

        

        quicksort(arr,low,e);

        quicksort(arr,s,high);

    }

    

    static int[] mergesort(int[]arr)

    {

        if(arr.length==1)

        {

            return arr;

        }

        int mid = arr.length/2;

        int[] left = mergesort(Arrays.copyOfRange(arr, 0,mid));

        int[] right = mergesort(Arrays.copyOfRange(arr, mid,arr.length));

        

        return merger(left,right);

    }

    

    private static int[] merger(int[] first,int[] second)

    {

        int [] mix = new int [first.length + second.length];

        int j=0;

        int i=0;

        int k=0;

        while(i<first.length && j < second.length)

        {

            if(first[i] < second[j])

            {

                mix[k] = first[i];

                i++;

            }

            else

            {

                mix[k] = second[j];

                j++;

            }

            k++;

        }

        

        while(i<first.length)

        {

            mix[k] = first[i];

            i++;

            k++;

        }

        while(j<second.length)

        {

            mix[k] = second[j];

            j++;

            k++;

        }

        return mix;

    }

}
