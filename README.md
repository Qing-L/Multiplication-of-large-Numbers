Multiplication-of-large-Numbers
===============================

//the functon of this application is multiplying large numbers, it's used c++ program.
#include <iostream>
#include <string>  
using namespace std; 
 
#define N 100 //宏定义 
  
void string_to_int(int *a , string ch)//将存储在string型数据中的数值赋值给int型数组
{  
    int len = ch.length();  //调用string类中的length（）函数求字符串长度
    int i = 0, term = 0;  
    for(i = 0 ; i < N ; i++)
	{  
        a[i] = 0;  //将int型数组中的值全部赋值为0
    }  
  
    for(i = 0 ; i < len ; i++){  
        term = ch[i];  
        a[len-i-1] = (term - '0');  //将字符串中的数据转换为int型，并逆序存入数组中
  
    }  
}   
  
int main()  
{  
    int a[N],b[N],c[2*N];  //a存被乘数，b存乘数，c存运算结果
	int len1,len2;//len1为被乘数的长度，len2为乘数的长度
    string ch1,ch2;  //ch1存被乘数，ch2存乘数
    int i = 0 , j =0;  
    cout<<"被乘数:";  
    cin>>ch1;  
    cout<<"乘数:";  
    cin>>ch2; 
	len1=ch1.length();
	do
	{
	    if(len1>N)  
		{
		    cout<<"被乘数长度溢出，请重新输入！"<<endl;
	     	cout<<"被乘数:";
	    	cin>>ch1;
	    	len1=ch1.length();
		}
	}while(len1>N);
	len2=ch2.length();
		do
	{
	    if(len2>N)  
		{
		    cout<<"被乘数长度溢出，请重新输入！"<<endl;
	     	cout<<"被乘数:";
	    	cin>>ch2;
	    	len1=ch2.length();
		}
	}while(len2>N);

    string_to_int(a , ch1);  
    string_to_int(b , ch2);  
      
    for(i = 0 ; i < 2*N ; ++i)
	{  
        c[i] = 0;  //将c全部赋值为0
    }  
    for(i = 0 ; i < N ; ++i)
	{  
        for(j = 0 ; j < N ; ++j)
		{  
            c[i+j] += a[i] * b[j]; //分别将数组中的值相乘并存入c数组中 
        }  
    }  
    for(i = 0 ; i < 2*N -1 ; ++i)
	{  
        c[i+1] += c[i] /10;//将后一位数据的进位加到前一位数据中  
        c[i] = c[i] % 10;  //后一位数据进位后的值
    }  
    j = 2*N -1;  
  
    while(c[j] == 0)    
               j--;    //从数组后面一直检测到不为0，再退出循环
    for(i = j;i >= 0; --i)    
           printf("%d",c[i]); //逆序输出   
    printf("\n");    
    return 0;    
}  
