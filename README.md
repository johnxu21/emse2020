# Scripts for mining Integrated Commits
This repository contains scripts used to mine integrated commits between any two connected repositories. For example mainline (**variant1**) and fork (variant2). **variant1** and **variant2** can be interchanged. For any two connected repositories, the scripts are able to identify the following commits in the order below: 

* Pull requests (PR) integration and their commits: source = variant2, destination = variant2.
	* Merged pull requests 
	* Squashed pull requests
	* Rebased pull requests
	* The script is also able determine
* Git integration
	* Merge/Rebase commits
	* Cherry-picked commits. The source and destination of the cherry-picked commits is also identified.
* Unique Commits for variant1 and variant2.

## How to run
* Import the project into any of your favorite editors. 
* The code uses the following libraries: **json-simple-1.1.jar**, **joda-time-2.0.jar**. The libraries should be included in the build path of the project. 
* The main project can be found in in the file **pr/IntegratedCommits.java**.
* You need to put your GitHub token in the file **util/Constants.java**. Here is a site to guide you in generation a [GitHub token]( https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token#creating-a-token). If you are running a commit heavy project, you might want to use more than one token otherwise the execution of the project with encounter a **GitHub rate limit** exception. Borrow a token from a friend. **The project will not run without a GitHub token(s)**
* In the main file **pr/IntegratedCommits.java**, change lines 24 and 25 for your variant pair. You can uncomment lines 30 to 44 and then comment out lines 27 and 28.
* You can also choose to determine code integration within a given time interval. For example, if you want to know how a given PR was integrated, you can change the **startDate** and the **stopDate** to dates around the merge date of the pull request.


## Example Outputs 
### Pair 1
**variant1** = getodk/collect (Destination)  
**variant2** = grzesiek2010/collect (Source)  
**Fork-Date** = 2016-12-02T11:26:41Z  
**Stop-Date** = 2020-01-01T00:00:00Z  

**Merged PR**  
PR-3531 : MergeCommit - 0f6558c0 :  MergeDate-2019-12-16T09:45:03Z : #Commits = 2  
Merged Commits | [b87c46ba, 0f96afbe]  

**Squashed PR**
PR-3462 : MergeCommit - 1ab3fe3e : MergeDate-2019-12-03T10:10:20Z : #Commits = 3  
SquashedCommit | [PRCommits]  
1ab3fe3e | [3508d2e8, f44f5e9d, 1d912dd4]  


**Rebased PR**  
PR-3434 : MergeCommit-56f4623d :  MergeDate-2019-11-05T14:14:16Z : #Commits = 5  
|prCommit : baseRepoCommit|   |965a0728:56f4623d|a2a92d30:e1e19a71|55d63aaa:1c9e54ea|86a93057:6b34bb0c|42267310:9fa9bc55|  

#### Summary of Commit Integration
**PR Integrated Commits**    
#MergedPR = 95 | #MergedPRCommits = 444   
#SquashedPR = 441 | #SquashedPRCommits = 1071  
#RebasedPR = 27 | #RebasedPRCommits = 161

**Git Integrated Commits**  
Number of git merge/rebased commits = 1305  
Number of git cherry-picked commits = 0  

**Unique commits**  
variant1 Unique commits = 3,051  
variant2 Unique commits = 1,305  

### Pair 2
**variant1** = k9mail/k-9 (Destination)  
**variant2** = philipwhiuk/k2 (Source)  
**Fork-Date** = 2018-01-17T20:06:10Z
**Stop-Date** = 2018-01-17T20:07:10Z

**Squashed PR**  
PR-3078 : MergeCommit-e80aa401 : MergeDate-2018-01-17T20:07:10Z : #Commits = 3  
SquashedCommit | [PRCommits]  
e80aa401 | [74156dc4, cc9d2cbf, 7ee7ba6e]  

#### Summary of Commit Integration
**PR Integrated Commits**    
#MergedPR = 0 | #MergedPRCommits = 0   
#SquashedPR = 1 | #SquashedPRCommits = 3  
#RebasedPR = 0 | #RebasedPRCommits = 0
  
**Git Integrated Commits**  
Number of git merge/rebased commits = 1  
Number of git cherry-picked commits = 0  

**Unique Commits**  
uniqueCommitsVariant1_size = 1  
uniqueCommitsVariant2_size = 1

