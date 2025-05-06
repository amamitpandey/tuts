CodeTest

## to see longest sequence
```

        int[] int1 = {1, 2, 4, 3, 6, 22, 5, 33};
        Arrays.sort(int1);
        for (int i = 0; i < int1.length; i=i+2) {
            if((i+1)==int1[i]){
                System.out.println(int1[i]);
            }
        }
```
## anagram : suffal words

```
        String s1 = "one";
        String s2 = "eno";
        char[] chars1 = s1.toCharArray();
        char[] chars2 = s2.toCharArray();
        Arrays.sort(chars1);
        Arrays.sort(chars2);

        if (Arrays.equals(chars1,chars2)){
            System.out.println("both s anagram");
        }else {
            System.out.println("both s not anagram"+chars1.toString()+"chars1.toString() "+chars2.toString());
        }


```
## Add Fractions

```
class Solution {
  
  public static int[] addFractions(int[] fraction1, int[] fraction2) throws IllegalArguementException {
   int[] result = { 0, 0};
   if(fraction2[1] == 0 || fraction1.length < 2){
       throw new IllegalArguementException(" not a valid fraction");
   }
   result[0] = (fraction1[0] * fraction2[1]) + (fraction1[1] * fraction2[0]);
   result[1] = (fraction1[1] * fraction2[1]);
   int hcf = findHCF(result[0],result[1]);
   result[0] = result[0]/hcf;
   result[1] = result[1]/hcf;
   return result;

}

public static int findHCF(int i1, int i2){
   int gcd = 1;
   for (int i = 1; i <= i1 && i <= i2; i++) {
       if(i1% i==0 && i2% i==0)
       { gcd = i;}
   }
   return gcd;
}


```
fibonacci
```
public static long fibonacci(int x)
{
   int sum = 0;
   int int1 = 0;
   int int2 = 1;
   if(x==1 || x==2){
       return 1;
   }
   for (int i = 1; i < x; i++) {
       sum = int1 + int2;
       int1 = int2;
       int2 = sum;
   }
   return sum;
}


```

ATOI


```
public class Solution
{
	/** 
	*Takes a string str and returns the int value represented by
	*the string
	*/

	public static int atoi(String str)
	{
		int result=0;
        int i=0;
   		int strLength = str.length();
   		int multiplier=1;
      
      if(strLength!=0 && str.charAt(0)=='-'){
        
       //negetive number 
        multiplier=-1;
        i++;
      }
      
      
      for(; i<strLength;i++)
      {
        
        char c=str.charAt(i);
        
        if(c<'0' || c>'9'){
         
          break;
        }
        
        result=result*10+c-'0';
      }
      
      return result*multiplier;
      
      
    };
      
```
Is power of 10
```
class Solution {
 //return true if x is power of ten else false
  public static boolean ispowerof10(int x)
  {
  for(int i=1;i<=x;i*=10)
   {
   if(i==x)
    return true;
   if(i>Integer.MAX_VALUE/10)
    return false;
   }
  return false;  
  }
```

first Non Repeating
```
class Solution {
  
  public static char findFirst(String input)throws IllegalArguementException 
  {
    Map<Character ,Integer> charFrequency=new HashMap<>(input.length());
   
      for(char c:input.toCharArray())
      {
        charFrequency.merge(c,1,Integer::sum);
      }
    for(char i:input.toCharArray())
    {
      if(charFrequency.get(i)==1)
        return i;
      
    }
    throw new IllegalArguementException("no repeating character ids found");
  }
```
anagrams
```
import java.io.*;
import java.util.*;
import org.junit.Test;

class Solution {
  
  @FunctionalInterface
  interface AnagramSolution {
    Set<Set<String>> group(List<String> words);
  }
  public static boolean doTestPass() {
    List<String> words= Arrays.asList("cat","dog","god","cat");
    AnagramSolution sol = (input) -> {
      Map<String, Set<String>> hashIndex = new HashMap<>();
      input.stream().forEach((word)-> {
      String sorted = sortCharacters(word);
      if(!hashIndex.containsKey(sorted))
      hashIndex.put(sorted, new HashSet<>());
      hashIndex.get(sorted).add(word);
      
      });
      return new HashSet<>(hashIndex.values());
    };
    Set<Set<String>> grouped= sol.group(words);
    boolean result= true;
   result = result && grouped.contains(new HashSet<>(Arrays.asList("cat")));
    result = result && grouped.contains(new HashSet<>(Arrays.asList("dog","god")));
    return result;
    };
    
    
  
  private static String sortCharacters(String word) {
      char[] chars = word.toCharArray();
   Arrays.sort(chars);
 return new String(chars);
    }
  
 public static void main(String[] args)
  {
   if(doTestPass()) {
    System.out.println("All tests passed");
   }else {
    System.out.println("Some test failed");
   }
  }
}
 
```

Solution-7 :Square Root

******************************************************************************************
import java.io.*;
import java.util.*;

/*
 * To execute Java, please define "static void main" on a class
 * named Solution.
 *
 * If you need more classes, simply define them inline.
 */

class Solution {
  
  
  public static double squareRoot(double x)
  {
  double threshold=.001;
  double guess=x/2.0;
   for(int iterations=500;(iterations>0 && Math.abs(guess*guess-x)>threshold);iterations--)
   {
   guess=guess-((guess*guess)-x)/(2*guess);
   }
  return guess;
  }
  public static boolean doTestPass()
  {
  double[] inputs={2,4,100};
  double[] expected_value={1.41421,2,10};
    double threshold=0.001;
    for(int i=0;i<inputs.length;i++)
    {
    if(Math.abs(squareRoot(inputs[i])-expected_value[i])>threshold)
                {System.out.printf("test failed for %f expected_value=%f;actual=%f\n",inputs[i],expected_value[i],squareRoot(inputs[i]));
                                   return false;
    }
                                   
  }
    System.out.println("All tests passed");
                                   return true;
  }
public static void main(String[] args) {
  doTestPass();
  }
}

```

Solution-8 :longest uniform substring
*****************************************************************************************
import java.io.*;
import java.util.*;

/*
 * To execute Java, please define "static void main" on a class
 * named Solution.
 *
 * If you need more classes, simply define them inline.
 */

class Solution {
  
  private static final Map<String,int[]> testCases=new HashMap<String,int[]>();
  static int[] longestUniformSubstring(String input)
  {
    int longestStart=-1;
    int longestLength=0;
    int ix=1;
    int length=input.length();
    while(ix<length)
    {
      int start=ix-1;
      int currentlength=1;
      while(ix<length && input.charAt(ix)==input.charAt(ix-1))
      {
        ix++;
        currentlength++;
      }
      if(currentlength>longestLength)
      {
        longestStart=start;
        longestLength=currentlength;
      }
      ix++;
    }
    return new int[]{longestStart,longestLength};
  }
public static void main(String[] args) {
  testCases.put("",new int[]{-1,0});
  testCases.put("10000111",new int[]{1,4});
  testCases.put("aabbbbCdAA",new int[]{2,4});
                boolean pass=true;
                for(Map.Entry<String,int[]> testCase :testCases.entrySet())
                    {
                      int[] result=longestUniformSubstring(testCase.getKey());
                      pass=pass && (Arrays.equals(result,testCase.getValue()));
                    }
                    if(pass)
                    {
                      System.out.println("all tests pass");
                      
                    }
                    else
                    {
                      System.out.println("there is a test failure");
                    }
  }
}


Solution-9 :PangramDetector
******************************************************************************************
import java.io.*;
import java.util.*;

/*
 * To execute Java, please define "static void main" on a class
 * named Solution.
 *
 * If you need more classes, simply define them inline.
 */

class Solution {
  private static class  PangramDetector
  {
    private static final String ALPHABET="abcdefghijklmnopqrstuvwxyz";
    public String findMissingLetters(String Sentence)
    {
      SortedSet<Character> missing=new TreeSet<Character>();
      for(int i=0;i<ALPHABET.length();i++)
      {
        missing.add(new Character(ALPHABET.charAt(i)));
        
      }
      String s=Sentence.toLowerCase();
      for(int i=0;i<s.length();i++)
      {
        missing.remove(new Character(s.charAt(i)));
        
      }
      StringBuilder sb=new StringBuilder();
      for(Character c:missing)
      {
        sb.append(c.charValue());
      }
      return sb.toString();
      
    }
  }
  public static void main(String []args) {
    
  PangramDetector pd = new PangramDetector();
    Boolean success = true;
    success = success && "".equalsIgnoreCase(pd.findMissingLetters("The quick brown fox jumps over the lazy dog"));
    

    if(success) {
      System.out.println("All test passed");
    }
    else {
      System.out.println("There is a test failure");
    }
  }
}


Solution 10] :Reverse String
***********************************************************************************************

class Solution {
  public static String reverseString(String str)
  {
    if(str.length()==0)
      return str;
     int strlength=str.length();
     StringBuilder sb=new StringBuilder(str.length());
     for(int i=str.length()-1;i>=0;i--)
     {
     sb.append(str.charAt(i));
     }
     return sb.toString();
  }
  public static boolean doTestPass()
  {
 String testString;
    String Solution;
    boolean result=true;
    result=result && reverseString("abcd").equals("dcba");
    result=result && reverseString("odd abcde").equals("edcba ddo");
    result=result && reverseString("even abcde").equals("edcba neve");
    result=result && reverseString("").equals("");
    return result;
  }
  public static void main(String[] args)
  {
  if(doTestPass())
  {
  System.out.println("All test pass");}
  else
    {
  System.out.println("Some tests fail");
}
}
}


Solution-11 :Run length encoding   
********************************************************************************************
import java.io.*;
import java.util.*;
import static org.junit.Assert.*;
import org.junit.*;
import org.junit.runner.*;

public class Solution {
  public static  String rle(String input)
  {
  if(input.isEmpty())
  {
  return "";
  }
    StringBuffer result=new StringBuffer();
    char lastSeen=0;
    int count=1;
    for(int i=0;i<input.length();i++)
    {
    char current=input.charAt(i);
      if(lastSeen==current)
      {
      count++;
      }
      else
      {
      if(lastSeen!=0)
      {
      result.append(lastSeen).append(count);}
      
      count=1;
      lastSeen=current;
      }}
  result.append(lastSeen).append(count);
  return result.toString();
    }
  @Test
  public    void doTestPass()
  {
assertEquals("",rle(""));
assertEquals("a1",rle("a"));
assertEquals("a3",rle("aaa"));
assertEquals("a3b3a2d1",rle("aaabbbaad"));
  }
  public static void main(String[] args) throws InterruptedException 
  {
  JUnitCore.main("Solution");
  }
}




Solution-12 :Second smallest
***********************************************************************************************


public class Solution {
public static int secondSmallest(int[] x)
{
if(x.length<2)
{return (0);}
int smallest=Integer.MAX_VALUE;//max 32 bit integer
int secSmallest=Integer.MAX_VALUE;
int Element;
for(int i=0;i<x.length;i++)
{
Element=x[i];
if(Element<smallest)
{
secSmallest=smallest;
smallest=Element;
}
else if(Element<secSmallest)
{
secSmallest=Element;	
	}}
return secSmallest;
}
public static boolean doTestsPass()
{
int[] a={};
int[] b={0};
int[] c={0,1};
int[] d={-1,0,1,-2,2};
int[] e={1,1,2};
int[] f={Integer.MAX_VALUE};
int[] g={Integer.MIN_VALUE,0,Integer.MAX_VALUE};
boolean result=true;
result&=secondSmallest(a)==0;
result&=secondSmallest(b)==0;
result&=secondSmallest(c)==1;
result&=secondSmallest(d)==-1;
result&=secondSmallest(e)==1;
result&=secondSmallest(f)==0;
result&=secondSmallest(g)==0;
if(result)
{
System.out.println("All tests pass");	
}
else
{
System.out.println("There are test failures");
}
return result;
}
public static void main(String[] args)
{	
doTestsPass();
}
}



Solution-13 :Smallest number
***********************************************************************************
import java.io.*;
import java.util.*;
import org.junit.Assert;

class Solution {
  
public static int findmin(int a[])
    {
    if(a==null)
      throw new IllegalArgumentException("invalid input");
      return findMinInArray(a,0,a.length-1);
    }
public static int findMinInArray(int a[],int left, int right)
    {
  if(left==right)
    return a[left];
  if(left>right)
    return a[0];
  int mid=(left+right)/2;
  if(mid<right && a[mid]>a[mid+1])
    return a[mid+1];
  if(mid>left && a[mid-1]>a[mid])
    return a[mid];
  if(a[right]>a[mid])
    return  findMinInArray(a,left,mid-1);
  return  findMinInArray(a,mid+1,right);
    }  
  public static boolean doTestPass()
  {
  boolean result=true;
  result=result && (findmin(new int[]{3,4,5,6,1,2})==1);
    result=result && (findmin(new int[]{2,1})==1);
    result=result && (findmin(new int[]{1})==1);
    result=result && (findmin(new int[]{1,2,3,4,5,6})==1);
    result=result && (findmin(new int[]{4,1,2,3})==1);
    result=result && (findmin(new int[]{3,2,1,4})==1);
    try{
      findmin(null);
        result=false;
      }
   catch(Exception e)
      {
      result=result && true;
      }
    if(result)
    {System.out.println("All test pass");}
    else
    {System.out.println("Test Failed");}
  return result;
  }
  public static void main(String[] args)
  {
  doTestPass();
  }
}


Solution-14 :Power
****************************************************************************
import java.io.*;
import java.util.*;


class Solution {
  public static double power(double base,int exponent)
  {
    if(base==0) return 0;
    if(exponent==0) return 1;
     if(exponent==1) return base;
    int positiveExponent=(exponent<0)?exponent*-1:exponent;
    double result=(positiveExponent%2==0)?power(base*base,positiveExponent/2):base*power(base*base,(positiveExponent-1)/2);
    return exponent<0?1/result:result;
    
  }
  public static boolean doTestsPass()
  {
    double base[]={2,2,2.3,0,5.5,6.2};
    int exponent[]={4,-3,20,10,0,1};
    boolean doTestsPass=true;
    double tolerance=0.0001;
    for(int i=0;i<base.length;++i)
   {
     double actual=power(base[i],exponent[i]);
      double expected=Math.pow(base[i],exponent[i]);
      boolean currentResult=Math.abs(actual-expected)<tolerance;
      doTestsPass=doTestsPass && currentResult;
   
    
    if(!doTestsPass)
    {
      System.out.println("power("+"base[i]"+","+"exponent[i])"+ "failed"+"actual:"+actual+"expected:"+Math.pow(base[i],exponent[i]));
    }
    }
    return doTestsPass;
    
  }
  public static void main(String[] args) {
    if(doTestsPass())
    {
      System.out.println("all tests passed");
      
    }
    else
    {
      System.out.println("there is a test failure");
    }
  
  }
}


Solution-15 :Pascal Triangle   
*******************************************************************************
import java.io.*;
import java.util.*;
import org.junit.Test;
import org.junit.runner.JUnitCore;
import org.junit.*;
import org.junit.runner.*;


public class Solution {
  @Test public void doTestPass() {
    Assert.assertTrue(Solution.pascal(0,0)==1);
    Assert.assertTrue(Solution.pascal(1,2)==2);
    Assert.assertTrue(Solution.pascal(5,6)==6);
    Assert.assertTrue(Solution.pascal(4,8)==70);
    Assert.assertTrue(Solution.pascal(6,6)==1);
  }  
  public static Map<Integer, Map<Integer,Integer>> pascalHash = new HashMap<>();
  public static int pascal(int col,int row) {
    if(col==0||col==row) {
      return 1;
    }
    if(pascalHash.containsKey(col) && pascalHash.get(col).containsKey(row)) {
      return pascalHash.get(col).get(row);
    }
    final int pascalValue = pascal(col,row-1)+pascal(col-1,row-1);
    pascalHash.put(col,new HashMap<Integer,Integer>(row,pascalValue));
    return pascalValue;
  }
  public static void main(String[] args) {
    JUnitCore.main("Solution");
  }
}

Solution-16-Apache log   
*******************************************************************************
import java.io.*;
import java.util.*;

                                                                                                                                                                                                                                                                                                                                                                                  
class Solution {
  public static String findTopIpaddress(String[] lines)
  {
    Map<String,Integer> counter=new HashMap<>();
    Arrays.stream(lines).forEach((line)->
    {
      String ipAddress=line.split(" ")[0];
      Integer count=counter.getOrDefault(ipAddress,0);
      counter.put(ipAddress,count+1);});
    //method1: find max value first and filter by that
    StringJoiner sj=new StringJoiner(",");
   final Integer max=counter.entrySet().stream().max((p1,p2)->p1.getValue()>p2.getValue()?1:-1).get().getValue();
    counter.entrySet().stream().filter(p->max==p.getValue()).sorted((p1,p2)->p1.getValue()>p2.getValue()?1:-1).forEach(p->sj.add(p.getKey()));
    return sj.toString();
    //method 2: Iterate the map once
                               /*   max=null;
            List<String> topIpAddresses=new ArrayList<>();
            for(Entry<String,Integer> p:Counter.entrySet())
                                       {
                                         if(max==null || max<p.getValue())
                                         {max=p.getValue();
                                          topIpAddresses.clear();
                                          topIpAddresses.add(p.getKey());}
                                    else if(max==p.getValue())
                                        {topIpAddresses.add(p.getKey());}}
          Collections.sort(topIpAddresses);
               return String.join(",",topIpAddresses);}
               */
                                       }
    public static boolean doTestsPass()
                      {
      boolean testsPassed=true;
                       String lines[]=new String[]{
                         "10.0.0.1 - frank [10/Dec/2000:12:34:56 -0500] \"GET /a.gif HTTP/1.0\" 200 234",
                         "10.0.0.1 - frank [10/Dec/2000:12:34:57 -0500] \"GET /b.gif HTTP/1.0\" 200 234",
                         "10.0.0.2 - nancy [10/Dec/2000:12:34:58 -0500] \"GET /c.gif HTTP/1.0\" 200 234"};
                       String result=findTopIpaddress(lines);
                       if(!result.equals("10.0.0.1")){
                         testsPassed=false;
                       }
                       lines=new String[]
                       {"10.0.0.1 - frank [10/Dec/2000:12:34:56 -0500] \"GET /a.gif HTTP/1.0\" 200 234",
                         "10.0.0.1 - frank [10/Dec/2000:12:34:57 -0500] \"GET /b.gif HTTP/1.0\" 200 234",
                         "10.0.0.2 - nancy [10/Dec/2000:12:34:58 -0500] \"GET /c.gif HTTP/1.0\" 200 234",
                         "10.0.0.2 - nancy [10/Dec/2000:12:34:59 -0500] \"GET /c.gif HTTP/1.0\" 200 234",
                         "10.0.0.3 - logan [10/Dec/2000:12:34:59 -0500] \"GET /d.gif HTTP/1.0\" 200 234"};
                       result=findTopIpaddress(lines);
                if(!result.equals("10.0.0.1,10.0.0.2"))
                                         {testsPassed=false;}
                  if(testsPassed){System.out.println("Tests passed");
                                                        }
                                                        else
                                                        {
                                        System.out.println("Tests failed");}
                               return testsPassed;}
                                                           
  public static void main(String[] args) {
    doTestsPass();
  }
}
 


Solution-17-Walking ROBOTS
******************************************************************************************************************
import java.io.*;
import java.util.*;

                                                                                                                                                                                                                                                                                                                                                                                  
class Solution {
  public static Integer[] walk(String path) {
    Integer[] result={0,0};
    for(char ch:path.toCharArray()) {
      switch(ch) {
        case 'U': result[1]+=1;break;
        case 'D': result[1
