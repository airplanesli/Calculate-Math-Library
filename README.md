# Calculate-Math-Library
This is my very first coding project, done in the beginning of my AP computer science class.
//Author Rita Li
//Program that calculates many kinds of math equations
//Started August 26, 2021
public class Calculate {
	public static int square(int x) {
		int result;
		result=x*x;
		return result;
	}
	public static int cube(int x) {
		int result;
		result=x*x*x;
		return result;
	}
	public static double average(double x, double y) {
		double result= (x+y)/2;
		return result;
	}
	public static double average(double x, double y, double z) {
		double result= (x+y+z)/3;
		return result;
	//overloading
	}
	public static double toDegrees(double x) {
		double result= x*(180/3.14159);
		return result;
	}
	public static double toRadians(double x) {
		double result= x*(3.14159/180);
		return result;
	}
	public static double discriminant(double a, double b, double c) {
		double result= b*b-4*a*c;
		return result;
	}
	public static String toImproperFrac(int whole, int num, int deno) {
		int numerator=(whole*deno)+num;
		String improperFrac= numerator+"/"+deno;
		return improperFrac;
	}
	public static String toMixedNum(int num, int deno) {
		int whole= num/deno;
		int numerator= num % deno;
		String result= whole+"_"+numerator+"/"+deno;
		return result;
	}
	public static String foil(int w, int x, int y, int z, String n) {
	//(wn+x)(yn+z)
		String result="("+(w*y)+n+"^2+"+((w*z)+(x*y))+n+"+"+x*z+")";
		return result;
	}
	public static boolean isDivisibleBy(int x, int y) {
		if (y==0) {
			throw new IllegalArgumentException("Innapropriate Value. Can't divide by 0.");
		}
		boolean result=x%y==0;
		return result;
	}
	public static double absValue(double x) {
		if (x>=0) {
			double result= x;
			return result;
		}else {
			double result= -x;
			return result;
		}
	}
	public static double max(double x, double y) {
		if (x>=y) {
			double result= x;
			return result;
		}else {
			double result= y;
			return result;
		}
	}
	public static double max(double x, double y, double z) {
		if (x>=y && x>=z) {
			double result= x;
			return result;
		}else if (y>=z && y>=x) {
			double result= y;
			return result;
		}else {
			double result= z;
			return result;
		}
	}
	public static int min(int x, int y) {
		if (x<=y) {
			int result= x;
			return result;
		}else {
			int result= y;
			return result;
		}
	}
	public static double round2(double x) {
		//rounds double to two decimal places
		double res = x*1000;
		if (x>0) {
			res+=5; //res=res+5
		}else {
			res-=5;
		}
		res/= 10;
		res= (int) (res)/100.0;
		return res;
	}
	public static double exponent(double x, int y) { //this version will only work for positive exponents
		if (y<0) {
			throw new IllegalArgumentException("Not for this algorithm mate");
		}
		if (y==0) { 
			double result=1;
			return result;
		}else {
			double res= 1;
			for (int i=1; i<=y || i<=-y; i++) {
				res=res*x; 
			}
		if (y>0) {
			return res;
		}else {    //negative exponent
			res=1/res;
			return res;
		}
		}
	}
	public static int factorial(int x) {
		int res= x;
		if (x<0) {
			throw new IllegalArgumentException("Boohoo! Innapropriate value");
		}
		for (int i=1; i<x; i++) {
			res=res*i;
		}
		if (x==0) {
			return 1;
		}
		return res;
	}
	public static boolean isPrime(int x) {
		int factor= 2; //amount of factors a prime number has
		for (int y= 2; y<x; y++ ) { //y is the factor
			if (isDivisibleBy(x, y)==true) {
				factor+=1;
		}
		}
		if (factor==2) { //prime numbers only have 2 factors in total
			boolean result= true;
			return result;
		} else {
			boolean result= false;
			return result;
		}
	}
	public static int gcf(int x, int y) { //using Euclid's Algorithm
	    int rem; 
	    if (y==0) {
	    	int c= y;
	    	y=x;
	    	x=c;
	    }
	    if (x==0 && y==0) {
	    	return 0;
	    }
	    while (isDivisibleBy(x,y)==false) {
	    	rem=x%y;
	    	x=y;
	    	y=rem;
	    }
	    return (int)absValue(y);
	}
	public static double sqrt(double x) { //x>0
		double guess=x/2;
		if (x<0) {
			throw new IllegalArgumentException("Can't take square root of negative.");
		}
		while (absValue(x-guess*guess)>0.005) {
			guess= 0.5*(x/guess + guess);
		}
		return round2(guess);
	}
	public static String quadForm(int a, int b, int c) {
		double disc= discriminant(a, b, c);
		if (disc<0) {
			return "no real roots";
		} else if (disc==0) {
			double root= round2(-b/(2*a));
			String res= ""+root+"";
			return res;
		} else {
			double root= round2((-b+sqrt(disc))/(2*a));
			double root2= round2((-b-sqrt(disc))/(2*a));
			if (root2<root) {
			String res= ""+root2+" and "+root+"";
			return res;
			} else {
				String res= ""+root+" and "+root2+"";
				return res;
			}
		}
	}
}
