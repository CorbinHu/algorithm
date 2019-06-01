#### T38：报数
```java
// 递归方法
class Solution {
    public String countAndSay(int n) {
        String str = "1";
        // 1. 出口
        if(n==1) return str;
        // 2. 每层循环需要做的事
        str = countAndSay(n-1);
        int len = str.length();
        StringBuilder builder = new StringBuilder();   
        char pre = str.charAt(0); // 被比较的字符
        int count = 1; // 记录相同的数字
        for(int i=1;i<len;i++){
            char c = str.charAt(i); // 比较的字符
            if (c == pre){
                count++;
            }else{
                builder.append(count).append(pre);
                pre = c; 
                count = 1;
            }     
        }
        builder.append(count).append(pre);
        str = builder.toString();
        // 3.返回值是什么：返回上次报数
        return str;
    }
}
# 循环
class Solution {
    public String countAndSay(int n) {
        String str = "1";
        for (int j=2;j<=n;j++){
            int len = str.length();
            StringBuilder builder = new StringBuilder();   
            char pre = str.charAt(0); // 被比较的字符
            int count = 1; // 记录相同的数字
            for(int i=1;i<len;i++){
                char c = str.charAt(i); // 比较的字符
                if (c == pre){
                    count++;
                }else{
                    builder.append(count).append(pre);
                    pre = c; 
                    count = 1;
                }     
            }
            builder.append(count).append(pre);
            str = builder.toString();
        }
        return str;
    }
}
```
