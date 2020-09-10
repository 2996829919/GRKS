#include<bits/stdc++.h>
using namespace std;
#define max 100000
#define e 2.718282
#define pi 3.14159265 

char str[max];
int s1[max];
float conter(float n,float t)         //计算N的T次方 
{
	float sum=1;
	if(t==0)
	    return 1;
	else
	{
		for(int i=0;i<t;i++)
	        sum=n*sum;
	    return sum;
	}	    
}

float juge(char str[])                      //判断输入数字的进制 
{   int i = 0, len = 0, temp = 0;
	float number=0,answer=0;
	int mc_a=0,location=0;
	int length=strlen(str);
	for(int i=0;i<length;i++)                 //判断是否为小数 
	{
		if(str[i]=='.')
		{
			mc_a=i;
			break;
		}
	}	
	location=length-mc_a;
/////////////////////////////////////////////////////////////
	if(str[0]=='0'&&str[1]=='x')                //判断16进制 
	{		
	    if(str[2])
	    if(mc_a==0)	    
	    	for(int i=length-1,j=0;i>1;i--)
			{
			    switch(str[i])  
                {  
                    case 'a':
                    case 'A': temp = 10; break;
		            case 'b':  
                    case 'B': temp = 11; break; 
		            case 'c': 
                    case 'C': temp = 12; break;
		            case 'd':  
                    case 'D': temp = 13; break; 
		            case 'e':
                    case 'E': temp = 14; break;  
                    case 'f':
                    case 'F': temp = 15; break;  
                    default: temp = str[i]-'0'; break;  
        }  	
		        number=temp*conter(16,j++)+number;	
			}	
			    			
		else
		{
			for(int i=mc_a-1,j=0;i>1;i--)
			{
					switch(str[i])  
	                {  
	                    case 'a':
	                    case 'A': temp = 10; break;
			            case 'b':  
	                    case 'B': temp = 11; break; 
			            case 'c': 
	                    case 'C': temp = 12; break;
			            case 'd':  
	                    case 'D': temp = 13; break; 
			            case 'e':
	                    case 'E': temp = 14; break;  
	                    case 'f':
	                    case 'F': temp = 15; break;  
	                    default: temp = str[i]-'0'; break;  
	        }  	
			        number=temp*conter(16,j++)+number;
				}	
			    
			for(int i=mc_a+1,j=1;i<length;i++)
			{
					 switch(str[i])  
	                {  
	                    case 'a':
	                    case 'A': temp = 10; break;
			            case 'b':  
	                    case 'B': temp = 11; break; 
			            case 'c': 
	                    case 'C': temp = 12; break;
			            case 'd':  
	                    case 'D': temp = 13; break; 
			            case 'e':
	                    case 'E': temp = 14; break;  
	                    case 'f':
	                    case 'F': temp = 15; break;  
	                    default: temp = str[i]-'0'; break;  
	        }  	
			        answer=temp*conter(0.0625,j++)+answer;
			}		
		number=number+answer;
		return number;
	} 
}
//////////////////////////////////////////////////////////////// 
	else if(str[0]=='0'&&str[1]=='b')                //判断2进制 
	{
		if(mc_a==0)	    
	    	for(int i=length-1,j=0;i>1;i--)	
			    number=(str[i]-'0')*conter(2,j++)+number;				
		else
		{
			for(int i=mc_a-1,j=0;i>1;i--)	
			    number=(str[i]-'0')*conter(2,j++)+number;
			for(int i=mc_a+1,j=1;i<length;i++)
			    answer=(str[i]-'0')*conter(0.5,j++)+answer;
		}		
		number=number+answer;
		return number;
	}
	else if(str[0]=='0'&&(str[1]!='b'||str[1]!='x'))   //判断8进制
	{
		if(mc_a==0)	    
	    	for(int i=length-1,j=0;i>0;i--)	
			    number=(str[i]-'0')*conter(8,j++)+number;				
		else
		{
			for(int i=mc_a-1,j=0;i>0;i--)	
			    number=(str[i]-'0')*conter(8,j++)+number;
			for(int i=mc_a+1,j=1;i<length;i++)
			    answer=(str[i]-'0')*conter(0.125,j++)+answer;
		}		
		number=number+answer;
		return number;
	} 
	else{                                                //10进制 
		if(mc_a==0)	    
	    	for(int i=length-1,j=0;i>=0;i--)	
			    number=(str[i]-'0')*conter(10,j++)+number;				
		else
		{
			for(int i=mc_a-1,j=0;i>=0;i--)	
			    number=(str[i]-'0')*conter(10,j++)+number;
			for(int i=mc_a+1,j=1;i<length;i++)
			    answer=(str[i]-'0')*conter(0.1,j++)+answer;
		}		
		number=number+answer;
		return number;
	}
}
	
				float plus(float a,float b)               //加法
			{
				float result;
				result=a+b;
				return result;
			}
			float mins(float a,float b)              //减法 
			{
				float result;
				result=a-b;
				return result;
			}
float xf(float a,float b)               //乘法 
			{
				float result;
result=a*b;
return result;
}
float cf(float a,float b)                //除法 
{
float result;
result=a/b;
return result;
}
compare(int a,int b)                //比较数字 
{
	if(a>b)
	    cout<<a<<">"<<b;
	else if(a<b)
	    cout<<a<<"<"<<b;
	else
	    cout<<a<<"="<<b;
	cout<<endl;
}

int maxgy(int n,int m)               //最大公约数 
{
	int s,t;
	if(m>n)
	{
		t=m;
		m=n;
		n=t;
	}
	while(m!=0)
	{
		s=n%m;
		n=m;
		m=s;
	}
	return n;
}
int mingb(int x,int y)                 //最小公倍数 
{
	while(x!=y)
	{
		if(x>y)
		   x=x-y;
		else
		   y=y-x;
	}
	return x;
}
float duishu(float a,float b)          //对数运算 
{
	float result;
	result=log(a)/log(b);
	return result;
}
float miyun(float a,float b)          //幂运算 
{
	double result;
	result=pow(a,b);
	return result;
}
float sinw(float a)
{
	double b,result;
	b=a*pi/180;
	result=sin(b);
	return result;
}
float cosw(float a)
{
	float b,result;
	b=a*pi/180;
	result=cos(b);
	return result;
}
float tanw(float a)
{
	float b,result;
	b=a*pi/180;
	result=tan(b);
	return result;
}
//ax+b=c
float hanshu(float a,float b,float c)          //一元一次函数 
{
	if(a==0)
	    cout<<"语法错误！"<<endl;
	float result;
	c=c-b;
	result=c/a;
	return result;
}
float fanbi(float a,float b,float c)             //反比例函数 
{
	if(a==0)
	    cout<<"语法错误！！"<<endl;
	else
	    b=c/a;
	return b;
}
float ss1[2]; 
float yiyuaner(float a,float b,float c)        // ax2+bx+c=0;
{
	float result,p;
	p=sqrt(b*b-4*a*c);
	if(p<0)
	    cout<<"该方程无解！"<<endl;
	else if(p=0)
	{
		result=(-b)/(2*a);
		return result;
	 } 
	 else if(p>0)
	 {
	 	
	 	ss1[0]=(-b+p)/(2*a);
	 	ss1[0]=(-b-p)/(2*a);
	 	return *ss1;
	 }
	
}
int main()
{   int chose;
	cout<<"-------------------------------------------------------------------"<<endl;
	cout<<" 																  "<<endl;
	cout<<"                            科学计算器                             "<<endl;
	cout<<"                   1.进制转化(16/8/2->10)                          "<<endl; 
	cout<<"                   2.四则运算(16/10/8/2)                           "<<endl;
	cout<<"                   3.对数，幂运算，三角函数运算（10）              "<<endl;
	cout<<"                   4.比较运算，max公约数，min公倍数(16/10/8/2)     "<<endl;
	cout<<"                   5.函数运算(10)                                  "<<endl;
	cout<<"                   6.混合运算(10)                                  "<<endl;
	cout<<"																	  "<<endl;
	cout<<"-------------------------------------------------------------------"<<endl;
	char s1[1000],s2[1000],ch,label;
	float e1,e2;
	cout<<"请选择功能："<<endl; 
	while(cin>>chose){
		switch(chose)
		{
			 case 1:
			 	cout<<"-----------------------"; 
					cout<<"请输入待转化值："<<endl;
					cin>>s1;
					cout<<"转化为10进制值为："<<endl;
					cout<<juge(s1)<<endl; 
					break;
		    case 2:
		    	    cout<<"请输入："<<endl;
					cin>>s1;
					cin>>ch;
					cin>>s2;
		    	    if(ch=='+')
		    	    {
					    e1= juge(s1);
						e2= juge(s2);
						cout<<(e1+e2)<<endl;
		                	
					}
					else if(ch=='-')
		    	    {
					    e1= juge(s1);
						e2= juge(s2);
						cout<<(e1-e2)<<endl;
		                	
					}
					else if(ch=='*')
		    	    {
					    e1= juge(s1);
						e2= juge(s2);
						cout<<(e1*e2)<<endl;		                	
					}
					else if(ch=='/')
		    	    {
					    e1= juge(s1);
						e2= juge(s2);
						cout<<(e1/e2)<<endl;		                	
					}		    	    
		    	    break;
		    case 3:
		    	cin>>s1;
		    	cin>>label;
		    	cin>>s2;
		    	e1= juge(s1);
				e2= juge(s2);
		    	if(label=='l')
			     	duishu(e1,e2);        //对数运算 
		    	
		    	    break;
		    case 4: 
		            break;
		    case 5:
		    	    break;
		    case 6:
		    	    break;
		}
		   
		
	} 	
	
    	
} 
