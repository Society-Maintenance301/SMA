int max=arr[0];
   int sum=0;
   
   for(i=0;i<arr.length;i++)
   {
     if (max<arr[i])
       max=arr[i];
     sum=sum+arr[i];
   }
   result=max;
   mark_avg= sum/s;
   
   System.out.println(result);
   System.out.print(mark_avg);
