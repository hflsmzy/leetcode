## 1. 两数之和（哈希表）

我们创建一个哈希表，对于每一个 x，我们首先查询哈希表中是否存在 target - x，然后将 x 插入到哈希表中，即可保证不会让 x 和自己匹配。

哈希表

```java
class Solution {
​    public int[] twoSum(int[] nums, int target) {
​        Map<Integer,Integer> hashtable=new HashMap<Integer,Integer> ();
​        for (int i=0;i<nums.length;i++){
​            if (hashtable.containsKey(target-nums[i])){
​                return new int[]{i,hashtable.get(target-nums[i])};
​            }
​            hashtable.put(nums[i],i);
​        }
​        return new int[0];
​    }
}
```

## 2. 两数相加（链表）

主要的难点在于进位。

```java
class Solution {
​    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
​        int carry=0;
​        ListNode dummy=new ListNode(0);
​        ListNode cur=dummy;
​        while(l1!=null||l2!=null){
​            int n1=(l1!=null?l1.val:0);
​            int n2=(l2!=null?l2.val:0);
​            int sum=n1+n2+carry;
​            cur.next=new ListNode(sum%10);
​            cur=cur.next;
​            carry=sum/10;
​            if(l1!=null){
​                l1=l1.next;
​            }
​            if(l2!=null){
​                l2=l2.next;
​            }
​        }
​        if(carry>0){
​            cur.next=new ListNode(carry);
​        }
​        return dummy.next;
​    }
}
```

3. 无重复字符的最长子串

   ```
   class Solution {
   
   ​    public int lengthOfLongestSubstring(String s) {
   
   ​        int n=s.length();
   
   ​        int rk=-1,ans=0;
   
   ​        Set<Character> occ=new HashSet<Character>();
   
   ​        for (int i=0;i<n;i++){
   
   ​            if (i!=0){
   
   ​                occ.remove(s.charAt(i-1));
   
   ​            }
   
   ​            while(rk+1<n&&!occ.contains(s.charAt(rk+1))){
   
   ​                occ.add(s.charAt(rk+1));
   
   ​                rk++;     
   
   ​            }
   
   ​            ans=Math.max(ans,rk-i+1);
   
   ​        }
   
   ​        return ans;
   
   ​        
   
   }
   
   }
   ```

   