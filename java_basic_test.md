
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

양의 정수 `x`가 하샤드 수이려면 `x`의 자릿수의 합으로 `x`가 나누어져야 합니다. 예를들어 10의 자릿수 합은 1+0이고, 
10은 1로 나누어 떨어지므로 10은 하샤드 수입니다.
`isHarshad`함수는 양의 정수 `num`을 매개변수로 입력받습니다. 이 `num`이 하샤드수인지 아닌지 판단하는 함수를 완성하세요.
예를들어 `num`이 10, 12, 18이면 `True`를 리턴 11, 13이면 `False`를 리턴하면 됩니다.

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
}
```


- 문제

높이만큼 별 출력 (역순)

```java
public static void main(String[] args) {
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
}
```


- 문제 

`reverseInt` 메소드는 `int`형 `n`을 매개변수로 입력받습니다.
`n`에 나타나는 숫자를 큰것부터 작은 순으로 정렬한 새로운 정수를 리턴해주세요.
예를들어 `n`이 `118372`면 `873211`을 리턴하면 됩니다.
`n`은 양의 정수입니다.

```java
public static void main(String[] args) {		
	int n = 118372;
	String nStr = Integer.toString(n);
	int[] arr = new int[nStr.length()];
	
	for (int i=0; i < arr.length; i++) {
		nStr.substring(i, i+1);
		arr[i] = Integer.parseInt(nStr.substring(i, i+1));
	}
	
	Arrays.sort(arr); //112378
		    
	int temp;
	for (int i = 0; i < arr.length / 2; i++) {
		temp = arr[i];
		arr[i] = arr[(arr.length - 1) - i];
		arr[(arr.length - 1) - i] = temp;
	}
    
	String ret="";
	for (int val : arr) {
		ret += Integer.toString(val);
	}
	System.out.println(ret);
}
```

- 문제

`getMinMaxString` 메소드는 `String`형 변수 `str`을 매개변수로 입력받습니다.
`str`에는 공백으로 구분된 숫자들이 저장되어 있습니다.
`str`에 나타나는 숫자 중 최소값과 최대값을 찾아 이를 `"(최소값) (최대값)"`형태의 `String`을 반환하는 메소드를 완성하세요.
예를들어 `str`이 "1 2 3 4"라면 "1 4"를 리턴하고, "-1 -2 -3 -4"라면 "-4 -1"을 리턴하면 됩니다.

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


**문제 중 `sort()` 이용 안하고 해보겠다고 삽질 좀 했던 문제**

- 문제

`reverseStr` 메소드는 `String` 형 변수 `str` 을 매개변수로 입력받습니다.
`str` 에 나타나는 문자를 큰것부터 작은 순으로 정렬해 새로운 `String` 을 리턴해주세요.
`str` 는 영문 대소문자로만 구성되어 있으며, 대문자는 소문자보다 작은 것으로 간주합니다.
예를들어 str이 `"Zbcdefg"`면 `"gfedcbZ"`을 리턴하면 됩니다.

 ```java
public static void main(String[] args) {
	String str = "AcbduZH", newStr= "";
	char[] charArr = str.toCharArray(); 
	
	int l=0, u=0;
	char c;
	for (int i = 0; i < str.length(); i++ ){
		c = str.substring(i, i+1).charAt(0);
		charArr[i] = c;
		if ((int)c < 91 )
			u++;
		else 
			l++;
	}
	
	char[] charUpperArr = new char[u];
	char[] charLowerArr = new char[l];
	l = 0;
	u = 0;
	for (int i = 0; i < str.length(); i++ ){
		if ((int)charArr[i] < 91 ){
			charUpperArr[u] = charArr[i];
			u++;
		} else { 
			charLowerArr[l] = charArr[i];
			l++;
		}
	}
	
	String lstr= "", ustr= "";
	if (charLowerArr.length > 0) {
		java.util.Arrays.sort(charLowerArr);
		lstr = String.valueOf(reverseCharArr(charLowerArr));
	}
	if (charUpperArr.length > 0) {
		java.util.Arrays.sort(charUpperArr);
		ustr = String.valueOf(reverseCharArr(charUpperArr));
	}
	
	newStr = lstr + ustr;
	//System.out.println("출력 : "+newStr);
	return newStr;


	//쉬운방법 (참고용)
//	String wordSt = "AcbduZH";
//    char[] word = wordSt.toCharArray();
//    for(int i=0;i<(word.length-1);i++){
//        for(int j=i+1;j>0;j--){
//        	System.out.println(" i = "+ i);
//        	System.out.println(" j = "+j);
//        	
//        	System.out.println("word[j] = "+word[j]);
//        	System.out.println("word[j-1] = "+word[j-1]);
//        	System.out.println("");
//            if(word[j]<word[j-1]){
//                char temp=word[j-1];
//                System.out.println("temp = "+temp);
//                word[j-1]=word[j];
//                word[j]=temp;
//                System.out.println("word[j] = "+word[j]);
//	        	System.out.println("word[j-1] = "+word[j-1]);
//	        	System.out.println("");
//            }
//        }
//    }
//    wordSt=String.valueOf(word);
//    System.out.println(wordSt);
		
}

public static char[] reverseCharArr(char[] ch) {
	char[] nch = new char[ch.length];
	int p= 0;
	for (int i = ch.length-1; i >= 0; i--) {
		nch[p] = ch[i];
		p++;
	}
	return nch;
}



/*
삽질의 흔적들.. 더 많지만 지저분해서 날림...
*/
public static String orderByChar(char[] arr ){
//	System.out.println("start orderByChar()...");
	
	String ret = "";
	//2개 이상일때
	if (arr.length > 2 ){
		for (int i=0; i < arr.length; i++) {
			int n = 0;
			char cn = arr[i];
//			char temp = arr[i];
			if ((i+1) < arr.length) {
				n = getCompareMinChar(cn, arr[i+1]);
				System.out.println("n 값 : "+ n);
				
				cn = arr[i+n];
				ret += cn;
				
			}
		}
		
	} else {
		ret += String.valueOf(arr[0]);
	}
	
	System.out.println("return orderByChar() : " + ret);
	
	return ret;
}

public static int getCompareMinChar(char a, char b ){
	System.out.println(a+" 비교 "+b);
//	int c = 0;
	if (transascii(a) < transascii(b) || transascii(a) == transascii(b))
		return 0;
	else
		return 1;
//	return c;
}

public static int transascii(char c) {
	return (int)c;
}
``````


`Arrays` 클래스의 `sort()` 가 아닌 직접 구현해보고 싶었는데 아직 알고리즘에 대한 지식이 많이 부족해서 
단순하게 풀려고 하다보니 더 꼬이고... 헛갈리고...

