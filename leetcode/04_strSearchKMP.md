// 第28题
```java
public class StrSearchKMP2 {
    public static void main(String[] args) {
        String pa = "abaabcac";
        String ta = "abcaabaabcacas";
        System.out.println(kmp_search(ta,pa));

    }

    // KMP算法

    // 生成next数组
    private static int[] getNext(char[] pa){
        int[] next = new int[pa.length];//储存前一位的最大前缀，也是下一比较的位置
        next[0] = -1;
        next[1] = 0;
        int k;//最长前缀的长度
        int i; //当前比较位
        for (i=2;i<pa.length;i++){
            k = next[i-1]; // 每次比较，k都初始化为当前位的前一个next值，表示前一位的最大前缀
            while(k!=-1){ // k=-1时，无前缀后缀
                // 当前位置的next值：由当前位置的前一个字符与其next值所对应的下标相比较。
                if (pa[i-1]==pa[k]){ //若当前位的前一个字符与第k个字符相等，则最大前缀+1
                    next[i] = k +1;
                    break;
                }else { // 若不相等，则k = 下次比较的位置
                    k = next[k];
                }
                next[i] = 0; //当k==-1而跳出循环时，next[i] = 0，否则next[i]会在break之前被赋值
            }
        }
        return next;
    }

    public static int kmp_search(String ta,String pa){
        char[] t = ta.toCharArray();
        char[] p = pa.toCharArray();
        int m = t.length;
        int n = p.length;
        int[] next = getNext(p);
        int j = 0,i = 0;

        while(i < m && j<n){ //遍历主串
            if (j == -1 || t[i] == p[j]){ // 若j=-1或字符相等，则指针i,j向后移动，继续比较
                i++;
                j++;
            }else { // 若不相等，指针i不动，将j移动到next[j]
                j = next[j];
            }
        }
        if(j == n){ // 说明以及匹配到子串
            return i-j;
        }
        return -1;

    }
}

```
