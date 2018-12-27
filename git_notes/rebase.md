# Rebasing 

Cherry-picking is nice but in most cases you don't really know what commit's you want 
to select or the order to apply them. In this case you can use interactive reabling. 

## Interactive rebasing 

Select the commits to be reased between selected baseline commit and your current 
location ( HEAD ). 
```bash 
git rebase -i <base_commit_id>
```
This will open the default test editor and you can select : 
- order to apply the commits 
- include/or not the commit `pick`


## Rebasing vs merging

There's a lot of debate about the tradeoffs between merging and rebasing in the development community. Here are the general pros / cons of rebasing:

##### Pros:

    Rebasing makes your commit tree look very clean since everything is in a straight line

##### Cons:

    Rebasing modifies the (apparent) history of the commit tree.

For example, commit C1 can be rebased past C3. It then appears that the work for C1' came after C3 when in reality it was completed beforehand.

