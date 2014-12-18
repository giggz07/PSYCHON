#include <bits/stdc++.h>
using namespace std;
 
int a[100005];
int primeFactors(int n)
{
	int count=0;
    while (n%2 == 0)
    {
        a[count]=2;
        n = n/2;
        count++;
    }
 
    for (int i = 3; i <= sqrt(n); i = i+2)
    {
        
        while (n%i == 0)
        {
            a[count]=i;
            n = n/i;
            count++;
        }
    }

    if (n > 2)
    {
       a[count]=n;
       count++;
	}
	return count;
}
 

int main()
{
    int t,n;
    scanf("%d",&t);
    while(t--)
    {
    	int c1=1,e=0,o=0;
    	scanf("%d",&n);
    int len = primeFactors(n);
    	for(int i=0 ; i<len-1 ; ++i)
    	{
    	//	cout<<a[i]<<" "<<a[i+1]<<" "<<c1<<endl;
    		if(a[i]==a[i+1])
    			c1++;
    		else
    			{
    				
    				if(c1&1)
    					o++;
    				else
    					e++;
    				c1=1;
    			}
    	}
   // cout<<c1<<endl;
    		if(c1&1)
    			o++;
    		else
    			e++;
    	
  //  cout<<len<<" "<<o<<" "<<e<<endl;
    if(e>o)
    	printf("Psycho Number\n");
    else
    	printf("Ordinary Number\n");
    }
    return 0;
}
