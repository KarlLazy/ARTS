# 1. Algorithm

- 1 . 
给定一个由整数组成的非空数组所表示的非负整数，在该数的基础上加一。
最高位数字存放在数组的首位， 数组中每个元素只存储一个数字。
你可以假设除了整数 0 之外，这个整数不会以零开头。
示例 1:
输入: [1,2,3]
输出: [1,2,4]
解释: 输入数组表示数字 123。
示例 2:
输入: [4,3,2,1]
输出: [4,3,2,2]
解释: 输入数组表示数字 4321。
class Solution {
    public int[] plusOne(int[] digits) {
        int len = digits.length;
        for(int i = len-1; i>=0; i--){
            if(digits[i]<9){
                digits[i]++;
                return digits;
            }
            else
                digits[i]=0;
        }
        int result[]=new int[len+1];
        result[0]=1;
        return result;
    }
}
真的挺难受的，看到这道题我的第一反应就是转int，因为题目要求就是简单的加1嘛。虽然隐约知道这样不好，int应该是存储不了int数组转化来的数据，但是还是试了一下，理所当然的失败了。然后差点一条道走到黑了，我竟然还想用大数来搞定这题。数组转为int已经是很耗时了，再用下大数就更没效率了。  
之后就直接对数组进行操作了，有进位就进位，全为9就扩充，还是没什么难度的，理清思路就行了，而且不要钻牛角尖。  
class Solution {
    public int[] plusOne(int[] digits) {
        if (digits.length == 0) return digits;
        int carry = 1, n = digits.length;
        for (int i = digits.length - 1; i >= 0; --i) {
            if (carry == 0) return digits;
            int sum = digits[i] + carry;
            digits[i] = sum % 10;
            carry = sum / 10;
        }
        int[] res = new int[n + 1];
        res[0] = 1;
        return carry == 0 ? digits : res;
    }
}
# 2. Review
# 3. Tip
# 4. Share
