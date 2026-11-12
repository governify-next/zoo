# Imago Flow Team Practices Agreement

Draft agreement. Page references are to *Imago Flow: a Basic Guide*, v1.0.

## 1. Practices in Imago Flow

### TP1. Require peer approval before merging

Obtain approval from at least one other team member before merging a pull or merge request.

**Scope** · Team and/or member  
**Window** · Weekly, by merge date

$$
\frac{\text{Number of PRs or MRs merged with prior teammate approval}}{\text{Number of merged PRs or MRs}} = 100\%
$$


### TP2. Have authors merge their own requests

Once a request is approved, the person who opened it performs the merge.

**Scope** · Team and/or member
**Window** · Weekly, by merge date

$$
\frac{\text{Number of merged PRs or MRs created and merged by their author}}{\text{Number of merged PRs or MRs created by their author}} = 100\%
$$


### TP3. Verify changes before and after merging (CI)

Run the required tests and CI checks before merging into main, then rerun them on the merged revision.

**Scope** · Team
**Window** · Weekly, by merge date

$$
\frac{\text{Number of merges that passed all checks}}{\text{Number of merges}} = 100\%
$$

### TP4. Follow the commit message format

Write a subject of 50 characters or fewer. Start with a capitalised imperative verb, describe the change and end without punctuation. 

**Scope** · Team or/and member
**Window** · Weekly, by commit date

$$
\frac{\text{Number of contribution commits with a valid message}}{\text{Number of contribution commits}} = 100\%
$$


## 2. Additional proposals

### TP5. Open pull requests regularly (Maybe merge PRs regularly)

Make changes available for review as work progresses so teammates can give timely feedback.

**Scope** · Team and/or member 
**Window** · Weekly, by request creation date

$$
\text{Number of PRs or MRs opened} \ge 1
$$

### TP6. Meet the line coverage target

When CI reports line coverage, verify that the revision being merged meets the 80% threshold. 

**Scope** · Team  
**Window** · weekly (Maybe use the last commit of the week)

$$
\frac{\text{Number of lines covered by tests}}{\text{Number of coverable lines}} \ge 80\%
$$

### TP7. Complete tasks regularly

Move completed tasks to Done as soon as the work is finished so the board reflects the team’s progress.

**Scope** · Team or/and member  
**Window** · Weekly, by date moved to `Done`

$$
\text{Number of tasks moved to Done} \ge 1
$$

### TP8. Limit work in progress per member

Keep at most one assigned task per member in the In Progress column.

**Scope** · Member  
**Window** · hourly

$$
\text{Number of assigned tasks in In Progress } \le 1
$$

### TP9. Log time on every completed task

Log each work session against the task.

**Scope** · Team
**Window** · Weekly

$$
\frac{\text{Number of completed tasks with time records}}{\text{Number of completed tasks}} = 100\%
$$

### TP10. Weekly minimum time spent on tasks

Track the time spent on tasks.

**Scope** · Member
**Window** · Weekly

$$
\sum_{\text{Task work sessions in the week}} \text{Session duration} \ge 4\text{ h}
$$
