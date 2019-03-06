class Solution {
public:
    int findLengthOfLCIS(vector<int>& nums) {
        int max = 1,i,j;//这道题是最长连续递增序列。max先设置好，i，j进行增长。
        int Max = 0;//这个是Max
        int len = nums.size();//NUM是先找到vector的长度。
        if (len ==1 ) return 1;//如果长度无法增长为1，那就返回1
        for(i = 0;i< len-1; i++){
            max = 1;//从头开始找，看看到哪里是增长的
            for(j = i;j < len-1;j++){//从第二个开始看是不是比前一个大
                if(nums[j+1] > nums[j]){
                    max +=1;  //
                    
                }
                else
                {
                    Max = max > Max? max:Max;//这一句兄弟用的很妙，确实是有认真复习过得，查了下的结果在要点里。这里用的比if语句就要巧妙，c++果然厉害。
                    break;
                }
            }
            Max = max > Max? max:Max;//同上
        }
        
        return Max;
    }
};
##要点
1、C++中的“?”表示判断，可代替简单的if...else...语句。

2、而“:”表示前后不同条件下的返回值。

例：C++中的？和：为运算符。 Exp1 ? Exp2 : Exp3;

Exp1、Exp2 和 Exp3 是表达式，请注意冒号的使用和位置。

? : 表达式的值取决于 Exp1 的计算结果。

如果 Exp1 为真，则计算 Exp2 的值，且 Exp2 的计算结果则为整个 ? : 表达式的值。

如果 Exp1 为假，则计算 Exp3 的值，且 Exp3 的计算结果则为整个 ? : 表达式的值。
