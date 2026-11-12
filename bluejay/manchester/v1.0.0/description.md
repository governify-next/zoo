# Manchester Team Practices Agreement

Draft agreement.

## 1. Weekly practices

### TP1. Commit regularly

Make at least one contribution commit each week.

**Scope** · Team and/or member  
**Window** · Weekly

$$
\text{Number of distinct non-merge commits} \ge 1
$$

### TP2. Add and delete code regularly

Add and delete code each week, counting lines across the TP1 commits ($C$).

**Scope** · Team and/or member  
**Window** · Weekly

$$
\begin{aligned}
\sum_{c \in C} \text{Lines added in } c &\ge 1 \\
\sum_{c \in C} \text{Lines deleted in } c &\ge 1
\end{aligned}
$$

### TP3. Open pull requests regularly

Open at least one pull request each week.

**Scope** · Team and/or member  
**Window** · Weekly, by pull request creation date

$$
\text{Number of pull requests opened} \ge 1
$$

### TP4. Get pull requests merged regularly

Get at least one of your pull requests merged each week.

**Scope** · Team and/or member  
**Window** · Weekly, by merge date

$$
\text{Number of pull requests merged} \ge 1
$$

### TP5. Comment on and approve pull requests regularly

Post a comment and submit an approval each week.

**Scope** · Team and/or member  
**Window** · Weekly, by comment or approval submission date

$$
\begin{aligned}
\text{Number of comments posted on pull requests} &\ge 1 \\
\text{Number of approval reviews submitted on pull requests} &\ge 1
\end{aligned}
$$

### TP6. Complete tasks regularly

Move at least one assigned task to `Done` each week.

**Scope** · Team and/or member  
**Window** · Weekly, by date moved to `Done`

$$
\text{Number of distinct tasks moved to Done} \ge 1
$$
