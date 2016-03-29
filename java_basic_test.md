
### 테스트 문제를 풀어봅시다

- 문제 
int 배열의 수 중 3으로 나누어지는 수를 반환하세요.

```java
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
```

- 문제 
가운데 글자를 되돌려주는 로직을 완성하세요. 문자열의 갯수가 홀수라면 1글자, 짝수라면 2글자를 

```java
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
```

- 문제 
양의 정수 x가 하샤드 수이려면 x의 자릿수의 합으로 x가 나누어져야 합니다. 예를들어 10의 자릿수 합은 1+0이고, 
10은 1로 나누어 떨어지므로 10은 하샤드 수입니다.
isHarshad함수는 양의 정수 num을 매개변수로 입력받습니다. 이 num이 하샤드수인지 아닌지 판단하는 함수를 완성하세요.
예를들어 num이 10, 12, 18이면 True를 리턴 11, 13이면 False를 리턴하면 됩니다.

```java
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
```

또 다른 방식, (풀고나서 인터넷으로 찾아봄)

```java
public static void main(String[] args) {  
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
```

- 문제 
int 배열의 평균을 구하세요.

```java
public static void main(String[] args) {
	int[] array = {23,14,456,12,4,56};
	int sum = 0;
	for (int val : array) {
		System.out.println(val);
		sum += val;
	}
	System.out.println("average" + sum / array.length);
}	
```

- 문제 
높이만큼 삼각별 출력

```java
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
```


- 문제 
reverseInt 메소드는 int형 n을 매개변수로 입력받습니다.
n에 나타나는 숫자를 큰것부터 작은 순으로 정렬한 새로운 정수를 리턴해주세요.
예를들어 n이 118372면 873211을 리턴하면 됩니다.
n은 양의 정수입니다.

```java
public static void main(String[] args) {		
	int n = 118372;
	String nStr = Integer.toString(n);
	int[] arr = new int[nStr.length()];
	
	for (int i=0; i < arr.length; i++) {
		nStr.substring(i, i+1);
		arr[i] = Integer.parseInt(nStr.substring(i, i+1));
//		System.out.println(nStr.substring(i, i+1));
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
```

- 문제
getMinMaxString 메소드는 String형 변수 str을 매개변수로 입력받습니다.
str에는 공백으로 구분된 숫자들이 저장되어 있습니다.
str에 나타나는 숫자 중 최소값과 최대값을 찾아 이를 "(최소값) (최대값)"형태의 String을 반환하는 메소드를 완성하세요.
예를들어 str이 "1 2 3 4"라면 "1 4"를 리턴하고, "-1 -2 -3 -4"라면 "-4 -1"을 리턴하면 됩니다.

```java
public static void main(String[] args) {
	
	String str = "5 6 -9 3 -5 9";
	String[] strArr = str.split(" ");
	int[] iArr = new int[strArr.length];
	
	for (int i=0; i < strArr.length; i++) {
//		System.out.println(strArr[i]);
		iArr[i] = Integer.parseInt(strArr[i]);
	}
//	System.out.println("-------------------------");
	
	Arrays.sort(iArr);
//	for (int s : iArr) {
//		System.out.println(s);
//	}
//	System.out.println("-------------------------");
	
	String nStr="";
	for (int i=0; i < iArr.length; i++) {
		if (i == 0 || i == (iArr.length-1)) {
			nStr += (Integer.toString(iArr[i]) + (i == 0 ? " ":""));
		}
	} 
	
	System.out.println(nStr);
	
}
```


**풀었던 문제 중에 아스키코드 값을 사용하지 않고 풀으려다가 삽질 좀 했던 문제 나갑니다.**


- 문제
reverseStr 메소드는 String형 변수 str을 매개변수로 입력받습니다.
str에 나타나는 문자를 큰것부터 작은 순으로 정렬해 새로운 String을 리턴해주세요.
str는 영문 대소문자로만 구성되어 있으며, 대문자는 소문자보다 작은 것으로 간주합니다.
예를들어 str이 "Zbcdefg"면 "gfedcbZ"을 리턴하면 됩니다.

 ```java
public static void main(String[] args) {
	String str = "Zbcdefg";
	
	String newStr = "";
	char[] charArr = new char[str.length()]; 
	
	for (int i=0; i < str.length(); i++) {
		charArr[i] = str.substring(i, i+1).charAt(0);
//		System.out.println("charat - "+str.substring(i, i+1).charAt(0));
	}
	
//	java.util.Arrays.sort(charArr); //안먹힘 
	
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
```