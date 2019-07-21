# 这是一级标题
## 这是二级标题
### 这是三级标题
#### 这是四级标题
##### 这是五级标题
###### 这是六级标题

**这是加粗的文字**
*这是倾斜的文字*`
***这是斜体加粗的文字***
~~这是加删除线的文字~~

![avatar](https://s2.ax1x.com/2019/07/21/e997VJ.jpg)

```java

class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        
        if (root == null){
            return result;
        }
        
        helper(root, 0 , result);
        return result;
    }
    
    private void helper(TreeNode node, Integer level,List<List<Integer>> result){
        if(node == null){
            return;
        }
        
        if(result.size() < level +1){
            result.add(new ArrayList<Integer>());
        }
        
        
        if(level%2==0){
            result.get(level).add(node.val);
        }else{
            result.get(level).add(0,node.val);            
        }
        
        helper(node.left, level+1, result);
        helper(node.right, level+1, result);
    }
    
    public List<List<Integer>> zigzagLevelOrder2(TreeNode root) {
        List<List<Integer>> result = new ArrayList<>();
        if(root == null){
            return result;
        }
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);
        int level = 0;
        while(!queue.isEmpty()){
            int size = queue.size();
            List<Integer> temp = new ArrayList<>();
            for(int i = 0; i<size;i++){
                TreeNode node = queue.poll();
                if(node.left!=null){
                    queue.add(node.left);
                }
                if(node.right!=null){
                    queue.add(node.right);
                }
                if(level%2 == 0){
                    temp.add(node.val);
                }else{
                    temp.add(0,node.val);

                }
                // System.out.print(node.val);
            }
            result.add(temp);
            level ++;

        }
        return result;
    }
}

```