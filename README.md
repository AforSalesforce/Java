import java.util.Scanner;
import java.math.*;
public class EggDrop {
	static void minWay(int e,int f)
	{
		int a[][]=new int[e+1][f+1];
		int MAX=100;
		for(int i=0;i<=e;i++)
		{
			a[i][1]=1;
			a[i][0]=0;
		}
		for(int j=1;j<=f;j++)
			a[1][j]=j;
		int min1=0,q=0,k=1,x=0;
		for(int p=2;p<=e;p++)
		{
			for(q=2;q<=f;q++)
			{
				a[p][q]=MAX;
				for(x=1;x<=q;x++)
				if(p>q)
				{
					a[p][q]=a[p-1][q];
				}
				else
				{
					min1=1+Math.max(a[p-1][x-1],a[p][q-x]);
					if(min1<a[p][q])
					{
						a[p][q]=min1;
					}
				}
			}
		}
		for(int l=0;l<=e;l++)
		{
			for(int m=0;m<=f;m++)
			{
				System.out.print(a[l][m]+" ");
			}
			System.out.println();
		}
	}


	public static void main(String[] args) {
		
		Scanner in=new Scanner(System.in);
		System.out.println("Entre the number of eggs");
		int e=in.nextInt();
		System.out.println("Enter the number of floor");
		int f=in.nextInt();
		minWay(e,f);

	}

}
