# KMP 算法原理和代码详解

## 视频地址
[KMP 算法原理和代码详解 作者：bilibili@左程云](https://www.bilibili.com/video/BV19Q4y1c7ko)（非常详细，推荐！）

## 代码

```java
public class KMP {
    public static int KMPSearch(String text, String pattern) {
        int[] next = nextArray(pattern);
        int m = pattern.length();
        int n = text.length();

        int i = 0; // index for text
        int j = 0; // index for pattern

        while (i < n && j < m) {
            if (pattern.charAt(j) == text.charAt(i)) {
                i++;
                j++;
            } else if (j > 0) {
                // next 可以回跳
                j = next[j];
            } else {
                // j == 0，即 next 无法再往回跳
                i++;
            }
        }

        return j == m ? i - j : -1;
    }

    private static int[] nextArray(String pattern) {
        int m = pattern.length();
        if (m == 1) {
            return new int[] { -1 };
        }
        int[] next = new int[m];
        next[0] = -1;
        next[1] = 0;
        int j = 0; // j 表示当前要和前一个字符 pattern.charAt(i - 1) 比对的下标
        while (i < m) {
            if (pattern.charAt(i - 1) == pattern.charAt(j)) {
                next[i] = j + 1;
                j++; // 这里的 j++ 其实是为了更新 j 为 next[i]，只不过正好是加 1 罢了。
                i++;
            } else if (j > 0) {
                // 此时 next[j] != -1，即仍然可以回跳
                j = next[j];
            } else {
                // 未匹配且 j == 0，无法回跳且没有合适的匹配前后缀
                next[i] = 0;
                // j == 0; // 这里 j 本身就是 0，因此不用再赋值了。
                i++;
            }
        }
        return next;
    }
}
```