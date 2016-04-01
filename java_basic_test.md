```java
package demoFirst;

import java.util.Arrays;

public class Demo {
	/*
	public static void main(String[] args) {
		String str1 = "hello";
		String str2 = "hello";
		
		final String strs = "";
		
		int [] arr = new int[4];
		arr[0] = 1;
		arr[1] = 2;
	}
	*/
	
	/*
	int seq;
	public Demo(int seq) {
		this.seq = seq;
	}
	public void run() {
		System.out.println(this.seq+" thread start.");
		try {
			Thread.sleep(1000);
		}catch(Exception e) {
			
		}
		System.out.println(this.seq+" thread end.");
	}
	
	public static void main(String[] args) {
		for(int i=0; i<10; i++) {
			Thread t = new Demo(i);
			t.start();
		}
		System.out.println("main end.");
	}*/
	
	
	/*
	private static ArrayList<Integer> numbersHasGenerator;

    public static void main(String[] args) {
        calculateNumbersHasGenerator();
        int sum = 0;
        for (int i = 0; i < 5001; i++)
            if (!hasGenerator(i))
                sum += i;
        System.out.println("합 : " + sum);
    }

    private static boolean hasGenerator(int num) {
        return numbersHasGenerator.contains(num);
    }   

    private static void calculateNumbersHasGenerator() {
        numbersHasGenerator = new ArrayList<Integer>();
        for (int i = 0; i <= 5000; i++) {
            String num = String.valueOf(i);
            int no = 0;
            for (int n = 0; n < num.length(); n++)
                no += Integer.parseInt(num.substring(n, n + 1));
            numbersHasGenerator.add(no + i);
        }
    }*/
	
	/*
		String str1 = "hello";		// 상수영역에 생성됨
	    String str2 = "hello";		// str2 는 "hello" 라는 값을 가진 상수영역의 String 을 검색하여 str1 의 값을 참조하게 됨
	    
	    String str3 = new String("hello");		// new 선언시 상수영역을 참조하지 않고 새로운 인스턴스를 힙 영역에 생성함
	    String str4 = new String("hello");		// new 선언으로 또 다시 새로운 힙 영역에 생성함
	    
	    System.out.println("------------------------------------ == 비교 (인스턴스의 주소를 비교함)");
	    
	    if (str1 == str2) {  // 같은 인스턴스를 참조하므로 결과는 true 
	        System.out.println("str1과 str2는 같은 레퍼런스입니다.");
	    }
	    if (str1 == str3) {  // str1과 str3은 서로 다른 인스턴스를 참조하므로 결과는 false 
	        System.out.println("str1과 str3는 같은 레퍼런스입니다.");
	    }
	    if (str3 == str4) {  // str3과 str4는 서로 다른 인스턴스를 참조하므로 결과는 false 
	        System.out.println("str3과 str4는 같은 레퍼런스입니다.");
	    }
	    
	    System.out.println("------------------------------------ equals() 비교 (인스턴스의 참조 값을 비교함)");
	    
	    if (str1.equals(str2)) {
	    	System.out.println("str1과 str2는 같은 값 입니다.");
	    }
	    if (str1.equals(str3)) { 
	        System.out.println("str1과 str3는 같은 값 입니다.");
	    }
	    if (str3.equals(str4)) { 
	        System.out.println("str3과 str4는 같은 값 입니다.");
	    }
	    if (str2.equals(str4)) { 
	        System.out.println("str2과 str4는 같은 값 입니다.");
	    }
	    
	    System.out.println("---------------------------------- ");
	    
	    //String 은 한번 생성되면 내부의 값이 변하지 않는다. (새로운 인스턴스를 생성하여 수정한 값을 돌려줌)
	    System.out.println(str1.substring(3));	// str1 의 값을 수정함
	    System.out.println(str1);		//	str1 의 값은 변하지 않았음
	*/
	
//	public static void main(String[] args) {
		
		/*String str1 = "hello";
		String str2 = "hello";
		
		if (str1.equals(str2)) {
			System.out.println("같은 값 입니다.");
			System.out.println("str1의 해시코드" + str1.hashCode());
			System.out.println("str2의 해시코드" + str2.hashCode());
		}
		
		System.out.println("--------------------------------------");
		
		String str3 = new String("hello");
		String str4 = new String("hello");
		
		if (str3.equals(str4)) {
			System.out.println("같은 값 입니다.");
			System.out.println("str3의 해시코드" + str3.hashCode());
			System.out.println("str4의 해시코드" + str4.hashCode());
		}*/
		
		
		
		/*
	    MyStrClass mc1 = new MyStrClass("hello");
	    MyStrClass mc2 = new MyStrClass("hello");
	    
	    if (mc1.equals(mc2)) {
	        System.out.println("mc1, mc2 같은 값 입니다.");
	    } else {
	        System.out.println("mc1, mc2 다른 값 입니다.");
	    }
	    
	    System.out.println(mc1.hashCode());
	    System.out.println(mc2.hashCode());
	    System.out.println("-------------------------------");
	    
	    MyStrClass mc3 = mc1;
	    MyStrClass mc4 = mc3;
	    
	    if (mc3.equals(mc4)) {
	        System.out.println("mc3, mc4 같은 값 입니다.");
	        
	    } else {
	        System.out.println("mc3, mc4 다른 값 입니다.");
	    }
	    
	    System.out.println(mc1.hashCode());
        System.out.println(mc2.hashCode());
        System.out.println(mc3.hashCode());
        System.out.println(mc4.hashCode());
        
        System.out.println("-------------------------------");
        */
        
		
/*		String str = "hello";
		MyClass mystr = new MyClass("hello");

		if (str.equals(mystr.str)) {
		    System.out.println("str 과 mystr 는 같다.");
		} else {
		    System.out.println("str 과 mystr 는 다르다."); 
		}*/
		
		
		
		/*
		
		if (str instanceof String) {
			System.out.println("String 인스턴스입니다.");
		}
		if (mystr instanceof String) {
			System.out.println("String 인스턴스입니다.");
		}
		

		MyClass mystr2 = new MyClass("hello");
		
		if (mystr2.equals(mystr)) {
		    System.out.println("mystr2 과 mystr 는 같다.");     // 실행
		} else {
		    System.out.println("mystr2 과 mystr 는 다르다.");
		}*/
		
//	}
	
	/*
	public static void main(String[] args){
		int[] array = {1,2,3,4,5,6,7,8,9};
		int divisor = 3;
		int[] ret;
		
		int i = 0;
		for(int val : array){
			if(val % divisor == 0){
				i++;
			}
		}
		
		ret = new int[i];
		i = 0;
		
	    for(int val : array){
	      if(val % divisor == 0){
	        ret[i] = val;
	        System.out.println(ret[i]);
	        i++;
	      }
	    }
	}
	*/
	
	
	/*
	public static void main(String[] args){
		String str = "power";
		String str1 = "testfiled";
		
		System.out.println(str.length());
		System.out.println(str.length() % 2);
		//나머지가 1이라면 홀수글자
		System.out.println(str.substring((str.length() / 2), (str.length() / 2)+1));
		//나머지가 0이라면 짝수글자
		System.out.println(str1.substring((str1.length() / 2)-1, (str1.length() / 2)+1));
		
	}
	*/
	
	/*양의 정수 x가 하샤드 수이려면 x의 자릿수의 합으로 x가 나누어져야 합니다. 예를들어 10의 자릿수 합은 1+0이고, 10은 1로 나누어 떨어지므로 10은 하샤드 수입니다.
		isHarshad함수는 양의 정수 num을 매개변수로 입력받습니다. 이 num이 하샤드수인지 아닌지 판단하는 함수를 완성하세요.
		예를들어 num이 10, 12, 18이면 True를 리턴 11, 13이면 False를 리턴하면 됩니다.*/
	/*
	public static void main(String[] args){
		int num = 352698;
		
		int jari = Integer.toString(num).length();
		int[] suArr = new int[jari];
		int sum = 0;
		
		for (int i = 0; i < jari; i++) {
			suArr[i] = Integer.parseInt(Integer.toString(num).substring(i, i+1));
			System.out.println(suArr[i]);
			sum += suArr[i];
		}
		System.out.println(sum);
		
		boolean ret;
		if (num % sum == 0) {
			System.out.println(true);
			ret = true;
		} else {
			System.out.println(false);
			ret = false;
		}
		
	}
	*/
	
	/*
	 * public static void main(String[] args) {  
  int num=Integer.parseInt(args[0]);  
  int su=0;  
  int jarisu=0,sum=0;  
    
  while(num>0)  
  {  
   su = num % 10; //입력된 숫자가 들어있는 변수(123)의 나머지 값을 su에 넣음.   
   sum += su;    //su를 sum에 더함.  
   num = num / 10;//입력된 숫자를 10으로 나눠서 num변수에 담음.  
   jarisu++; //반복될대마다 자리수가 증가됨.  
  }  
   System.out.println("자 릿 수 : " + jarisu); //출력  
   System.out.println("총 합 : " + sum); //출력  
 } 
	 */
	
//	public static void main(String[] args) {
//		int[] array = {23,14,456,12,4,56};
//		int sum = 0;
//		for (int val : array) {
//			System.out.println(val);
//			sum += val;
//		}
//		System.out.println("average" + sum / array.length);
//	}	
	
	
	/*
	 * 높이만큼 별 출력
	 */
	/*
	public static void main(String[] args) {
		
		int sum = 8, sumSub = 0;
		String star = "*";
		StringBuffer sb = new StringBuffer();
		
		for (int i=0; i < sum; i++) {
			sumSub = (i+1);
			while (sumSub > 0) {
				sb.append(star);
				sumSub--;
			}
			sb.append("\n");
		}
		System.out.println(sb.toString());
	}
	*/

	/*
	 * 높이만큼 별 출력 (역순)
	 */
	/*public static void main(String[] args) {
		int sum = 5;
		int sumSub = 0;
		String star = "*";
		StringBuffer sb = new StringBuffer();
		
		for (int i=0; i < sum; i++) {
			System.out.println("for start...");
			sumSub = sum-i;
			while(sumSub != 0){
				System.out.println("while start...");
				sb.append(star);
				sumSub--;
			}
			sb.append("\n");
		}
		System.out.println(sb.toString());
	}*/
	
	/*
	 * reverseStr 메소드는 String형 변수 str을 매개변수로 입력받습니다.
		str에 나타나는 문자를 큰것부터 작은 순으로 정렬해 새로운 String을 리턴해주세요.
		str는 영문 대소문자로만 구성되어 있으며, 대문자는 소문자보다 작은 것으로 간주합니다.
		예를들어 str이 "Zbcdefg"면 "gfedcbZ"을 리턴하면 됩니다.
	 */
	public static void main(String[] args) {
		String str = "Zbcdefg";
		
		String newStr = "";
		char[] charArr = new char[str.length()]; 
		
		for (int i=0; i < str.length(); i++) {
			charArr[i] = str.substring(i, i+1).charAt(0);
//			System.out.println("charat - "+str.substring(i, i+1).charAt(0));
		}
		
//		java.util.Arrays.sort(charArr);
		
		char[] nArr = new char[str.length()];
		char temp;
		for (int j=0; j < charArr.length; j++) {
			System.out.println(charArr[j] + "******* 비교 시작");
			for(int i=0; i < charArr.length; i++) {
				if (0 < String.valueOf(charArr[j]).compareTo(String.valueOf(charArr[i]))) {
					System.out.println("변경 시작");
					temp = charArr[j];
					charArr[j] = charArr[i];
					charArr[i] = temp;
					break;
				}
			}
			System.out.println("내부루프 끝");
		}
		System.out.println("-------------------------");
		
		for (char a : charArr) {
			System.out.println(a);
		}
	}
	
	
		/*
	public static void main(String[] args) {		
//		reverseInt 메소드는 int형 n을 매개변수로 입력받습니다.
//		n에 나타나는 숫자를 큰것부터 작은 순으로 정렬한 새로운 정수를 리턴해주세요.
//		예를들어 n이 118372면 873211을 리턴하면 됩니다.
//		n은 양의 정수입니다.
		
		int n = 118372;
		String nStr = Integer.toString(n);
		int[] arr = new int[nStr.length()];
		
		for (int i=0; i < arr.length; i++) {
			nStr.substring(i, i+1);
			arr[i] = Integer.parseInt(nStr.substring(i, i+1));
//			System.out.println(nStr.substring(i, i+1));
		}
		
		Arrays.sort(arr); //112378
		System.out.println("--------------------");
	    for (int val : arr) {
	    	System.out.println(val);
	    }
	    
		int temp;
	    for (int i = 0; i < arr.length / 2; i++) {
	    	System.out.println(i);
	    	
			temp = arr[i];
			System.out.println("temp - "+temp);
			  
			arr[i] = arr[(arr.length - 1) - i];
			System.out.println("arr[i] - "+arr[i]);
			  
			arr[(arr.length - 1) - i] = temp;
	    }
	    
	    System.out.println("--------------------");
	    for (int val : arr) {
	    	System.out.println(val);
	    }
	    
	    String ret="";
	    for (int val : arr) {
		    //System.out.println(val);
	      ret += Integer.toString(val);
	    }
	    
	    System.out.println(ret);
		
	}
	*/
	
	
	/*getMinMaxString 메소드는 String형 변수 str을 매개변수로 입력받습니다.
	str에는 공백으로 구분된 숫자들이 저장되어 있습니다.
	str에 나타나는 숫자 중 최소값과 최대값을 찾아 이를 "(최소값) (최대값)"형태의 String을 반환하는 메소드를 완성하세요.
	예를들어 str이 "1 2 3 4"라면 "1 4"를 리턴하고, "-1 -2 -3 -4"라면 "-4 -1"을 리턴하면 됩니다.*/
	/*public static void main(String[] args) {
		
		String str = "5 6 -9 3 -5 9";
		String[] strArr = str.split(" ");
		int[] iArr = new int[strArr.length];
		
		for (int i=0; i < strArr.length; i++) {
//			System.out.println(strArr[i]);
			iArr[i] = Integer.parseInt(strArr[i]);
		}
//		System.out.println("-------------------------");
		
		Arrays.sort(iArr);
//		for (int s : iArr) {
//			System.out.println(s);
//		}
//		System.out.println("-------------------------");
		
		String nStr="";
		for (int i=0; i < iArr.length; i++) {
			if (i == 0 || i == (iArr.length-1)) {
				nStr += (Integer.toString(iArr[i]) + (i == 0 ? " ":""));
			}
		} 
		
		System.out.println(nStr);
		
	}*/
	
	
}
```