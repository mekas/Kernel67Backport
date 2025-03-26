# Kernel67Backport Instruction
Name: .............
NIM: ..............

There two tasks for this assignment. 

## Task 1: Kernel Deployment (40%)
Previously on class, we have mentioned the necessity to deploy the kernel into a VM with FlorentRevest extension. 
1. Build the kernel with any .config configuration using Clang
2. Deploy the kernel with the extension
3. Capture the screenshot after the kernel is booted inside the VM. There are only two outputs either a Kernel Panic or Successfull boot which an initfs session is started. 
4. Create directory task1, put your screenshot there which named boot.jpg. -
5. Create a README.md inside which describe what kind of modification you did to make it boot successfully. Don't create README in case of kernel panic. In case of kernel panic score is 0.2. 

## Task 2: Kernel Backport Patching (60%)
There are two ways to solve this task: easy way which will net 0.2, and hard way which will net full 0.4. Start by creating task2 directory. Submission items related to task 2 will be put into this directory. 

###Easy Way (0.3)
1. Start from Kernel 6.6. Tag
2. Seek your target commit id by seeking through a git log. Your interest is in non merge commit which usually produce smaller commit size.
3. Seek information regarding the merge window of kernel 6.7, that will be your bound period when you're doing a git log. Otherwise the git log messages will still be huge. Alternatively you can bound the search by bounding the search by 6.6 to 6.7 tag. 
4. For the assignment the minimum line changes accepted is 30 lines. So perharps you need to mix several patches together in case that the patch is too small, while still limiting commit changes not be too large. 
5. You will also need to mix git rev-list, git show, git diff to ensure the commit is indeed suit your needs. 
6. Now this is the true trick for easy way solving. Update your repo to 1 or several commits before your commit target. You can use checkout command for this. Ensure with git diff as final checking. 
7. Run git diff <commit_ids> --stat > patch_<commit_id>.diff
8. Merge manually all change, then recompile again. 
8. Run git diff <commit_ids> --stat > patch\_now.diff

###Hard Way (0.6)
1. The same as Easy Way except for step 6. So you must still in base 6.6 tag
2. Conduct git diff to know changes needed to the current tag. It will be much larger compared to the easy way. Therefore the trick here is to pick suitable commit\_id. How to do that I leave it to you. 
3. Properly understand your commit target by running and examining detailed git log, git show, and git diff. Not all changes are really related to the feature. It will be up to you to identify which changes of the commit will be integrated into the base repo. 
4. Merge the necessary changes to your repo. Then commit, but don't push. 
5. Find your own local commit by running Git Log again. 
6. Run git diff <your_current_commit_id> tags/v6.6 > patch\_hard.diff
7. Create a README which shown your self reflection regarding task 2 completion
