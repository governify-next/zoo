**https://github.com/governify-next/zoo/tree/main/bluejay/uclm/isii/2026-2027/v1.0.0**

## **Changelog**

| **Version** | **Date**       | **Description**                  | **Authors**                             |
| ----------- | -------------- | -------------------------------- | --------------------------------------- |
| **v1.0**    | **2026-09-25** | **Complete initial description** | **Javier Fernández, Antonio Rodríguez** |

## <a name="_page3_x72.00_y72.00"></a>**Introduction and context**

This document provides a detailed explanation on how to correctly interpret the TPA in Bluejay. Some definitions in relation to the Governify ecosystem that will facilitate the understanding of the TPA are explained in the following points:

1. A **TPA (Team Practices Agreement)** is made up of **TPs (Team Practices)**.
2. Each **TP** is made up of one **guarantee.**
3. A **guarantee** defines what a work team must comply with to ensure its proper functioning.
4. Each **guarantee** needs an **objective**, which will be using one or more **metrics** along with a threshold value, and a **period** that defines the time boundary for the compliance of the guarantee.
5. Each **metric** represents a single variable that will be measured from a project.

> **Example**
>
> If we want the work team to make at least one pull request weekly, that will be our **TP**, which will be included in the **TPA**. We will then need to create a **guarantee,** which will have an **objective** that will need a **metric** to represent the variable “number of pull requests created by the team” (we will give it the ID “NUMBER_PR_CREATED”) and a **period**, which will be “weekly” in this case.
>
> Given all the previous context, our **guarantee’s objective** would be “NUMBER_PR_CREATED >= 1” and the **period** would be “weekly”.

---

# Summary

- TPa: At least 75% of 'In Progress' issues with the 'Task' type must match creation of a branch. (by Team, Hourly)
- TPb: At least 75% of 'In Progress' issues with the 'Task' type must have different branches associated.(by Team, Hourly)
- TPc: At least 75% of 'In Review' issues with the 'Task' type must match creation of a Pull Request.(by Team, Hourly)
- TPd: At least 75% of 'Done' issues with the 'Task' type must match merge of a Pull Request.(by Team, Hourly)
- TPe: Number of “In Progress” issues with the 'Task' type (by Member, Hourly)
- TPf: Number of “Done” issues with the 'Task' type (by Member, Weekly)
- TPg: Percentage of approved merged PR (by Team, Weekly)
- TPh.1: Percentage of approved merged PR (by Member, Weekly)
- TPh.2: Number of approved merged PR (By Member, Weekly)

---

# **TPa: At least 75% of 'In Progress' issues with the 'Task' type must match creation of a branch. (by Team, Hourly)**

> **Rule:** When an issue with the "Task" type is moved to "In Progress", a branch associated to this issue must be created.

<div align="center">

| Specification |                                          |
| :------------ | :--------------------------------------- |
| **Guarantee** | `CORRELATION_INPROGRESSISSUES_NEWBRANCH` |
| **Scope**     | Team                                     |
| **Period**    | Hourly                                   |

</div>

### Application steps

1. An **issue** in the "Todo" column with the "Task" type is moved to the "In Progress" column.
2. A new branch is created from the "In Progress" issue using the **Development** section to link it automatically.

<div align="center">

|                                        Objective                                        |
| :-------------------------------------------------------------------------------------: |
| `COUNT_INPROGRESS_ISSUES_WITH_ASSOCIATED_BRANCHES / COUNT_INPROGRESS_ISSUES × 100 ≥ 75` |

</div>

**Where:**

- **COUNT_INPROGRESS_ISSUES_WITH_ASSOCIATED_BRANCHES**: Number of in progress issues with the "Task" type and associated branches.
- **COUNT_INPROGRESS_ISSUES**: Number of in progress issues with the "Task" type.

### Workflow example

1. The issue with the "Task" type called “Creation of pets for vets” is moved from the "Todo" column to the "In Progress" column.
2. The branch called "pets-form" is created inside the issue's **Development** section.

### Evaluation example

If the team has **5** "In Progress" issues with the "Task" type and **4** of them have an associated branch:

<div align="center">

$\displaystyle \text{Value} = \left(\frac{4}{5}\right) \times 100 = 80$%

</div>

Since 80% ≥ 75%, compliance is satisfied.

---

# **TPb: At least 75% of 'In Progress' issues with the 'Task' type must have different branches associated. (by Team, Hourly)**

> **Rule:** Each issue with the "Task" type in In Progress must have a different branch associated with it.

<div align="center">

| Specification |                                                   |
| :------------ | :------------------------------------------------ |
| **Guarantee** | `CORRELATION_BRANCHESASSOCIATED_INPROGRESSISSUES` |
| **Scope**     | Team                                              |
| **Period**    | Hourly                                            |

</div>

### Application steps

1. An issue in the "Todo" column with the "Task" type is moved to the "In Progress" column.
2. A new branch is created from the "In Progress" issue using the **Development** section, and will not be associated with any other issue with the "Task" type.

<div align="center">

|                                       Objective                                       |
| :-----------------------------------------------------------------------------------: |
| `COUNT_BRANCHES_ASSOCIATED_TO_INPROGRESS_ISSUES / COUNT_INPROGRESS_ISSUES × 100 ≥ 75` |

</div>

**Where:**

- **COUNT_BRANCHES_ASSOCIATED_TO_INPROGRESS_ISSUES**: Number of different branches associated to "In Progress" issues with the "Task" type.
- **COUNT_INPROGRESS_ISSUES**: Number of "In Progress" issues with the "Task" type.

### Workflow example

1. The issue with the "Task" type called “Creation of pets for vets” is moved from the "Todo" column to the "In Progress" column.
2. The branch called "pets-form" is created inside the issue's **Development** section, and will not be associated with any other issue with the "Task" type.

### Evaluation example

If the team has **3** unique branches linked to **4** "In Progress" issues with the "Task" type:

<div align="center">

$\displaystyle \text{Value} = \left(\frac{3}{4}\right) \times 100 = 75$%

</div>

Since 75% ≥ 75%, compliance is satisfied.

---

# **TPc: At least 75% of 'In Review' issues with the 'Task' type must match creation of a Pull Request. (by Team, Hourly)**

> **Rule:** When an issue with the "Task" type is moved to In Review, a Pull Request associated to that issue must be created.

<div align="center">

| Specification |                                     |
| :------------ | :---------------------------------- |
| **Guarantee** | `CORRELATION_INREVIEWISSUES_OPENPR` |
| **Scope**     | Team                                |
| **Period**    | Hourly                              |

</div>

### Application steps

1. An issue in the "In Progress" column with the "Task" type is moved to the "In Review" column.
2. A **pull request** is created.
3. New open pull request is associated to the "In Review" issue with the "Task" type using the **Development** section, either from the pull request or from the issue itself.

<div align="center">

|                                     Objective                                      |
| :--------------------------------------------------------------------------------: |
| `COUNT_INREVIEW_ISSUES_WITH_ASSOCIATED_OPEN_PR / COUNT_INREVIEW_ISSUES × 100 ≥ 75` |

</div>

**Where:**

- **COUNT_INREVIEW_ISSUES_WITH_ASSOCIATED_OPEN_PR**: Number of "In Review" issues with the "Task" type and associated open pull request.

- **COUNT_INREVIEW_ISSUES**: Number of "In Review" issues with the "Task" type.

### Workflow example

1. The issue with the "Task" type called "Creation of user" is moved from the "In Progress" column to the "In Review" column.
2. The pull request called "user-form" is created.
3. The open pull request called "user-form" is associated to the issue with the "Task" type called “Creation of user” located in the "In Review" column.

### Evaluation example

If the team has **4** "In Review" issues with the "Task" type and **3** of them have an associated open pull request:

<div align="center">

$\displaystyle \text{Value} = \left(\frac{3}{4}\right) \times 100 = 75$%

</div>

Since 75% ≥ 75%, compliance is satisfied.

---

# **TPd: At least 75% of 'Done' issues with the 'Task' type must match merge of a Pull Request.(by Team, Hourly)**

> **Rule:** When an issue with the 'Task' type is moved to Done, the Pull Request associated to the issue must be merged.

<div align="center">

| Specification |                                   |
| :------------ | :-------------------------------- |
| **Guarantee** | `CORRELATION_DONEISSUES_MERGEDPR` |
| **Scope**     | Team                              |
| **Period**    | Hourly                            |

</div>

### Application steps

1. An issue in the "In Review" column with the "Task" type is moved to the "Done" column.
2. The pull request associated to the issue is merged.

<div align="center">

|                                  Objective                                   |
| :--------------------------------------------------------------------------: |
| `COUNT_DONE_ISSUES_WITH_ASSOCIATED_CLOSED_PR / COUNT_DONE_ISSUES × 100 ≥ 75` |

</div>

**Where:**

- **COUNT_DONE_ISSUES_WITH_ASSOCIATED_CLOSED_PR**: Number of "Done" issues with the "Task" type and associated merged pull request.

- **COUNT_DONE_ISSUES**: Number of "Done" issues with the "Task" type.

### Workflow example

1. The issue with the "Task" type called “Creation of admin” is moved from the "In Review" column to the "Done" column.
2. The open pull request called "admin-form" is merged.

### Evaluation example

If the team has **4** "Done" issues with the "Task" type and **3** of them have an associated merged pull request:

<div align="center">

$\displaystyle \text{Value} = \left(\frac{3}{4}\right) \times 100 = 75$%

</div>

Since 75% ≥ 75%, compliance is satisfied.

---

# **TPe: Number of “In Progress” issues with the 'Task' type (by Member, Hourly)**

> **Rule:** A developer should only be working on one issue with the "Task" type at a time.

<div align="center">

| Specification |                                          |
| :------------ | :--------------------------------------- |
| **Guarantee** | `NUMBER_INPROGRESSISSUES_HOURLY_UNDER_1` |
| **Scope**     | Member                                   |
| **Period**    | Hourly                                   |

</div>

### Application steps

1. An issue with the "Task" type is moved to the "In Progress" column only if we are not working on another task.

<div align="center">

|              Objective              |
| :---------------------------------: |
| `COUNT_INPROGRESSISSUES_MEMBER ≤ 1` |

</div>

**Where:**

- **COUNT_INPROGRESSISSUES_MEMBER**: Number of issues in the “In Progress” column with the "Task" type by member.

### Workflow example

1. The member Alexander does not have any issues “In Progress” with the "Task" type.
2. He decides to move an issue with the "Task" type that is assigned to him into the "In Progress" column.
3. He wants to take on a new issue with the "Task" type, but prior to moving it into "In Progress", he must move the issue with the "Task" type that is already "In Progress" into the “In Review” column. Then, he will be able to start a new task.

### Evaluation example

If Alexander has **2** "In Progress" issues with the "Task" type, the value is **2**. Since $2 \nleq 1$, compliance is not satisfied.

---

# **TPf: Number of "Done” issues with the 'Task' type (by Member, Weekly)**

> **Rule:** Each developer should be finishing at least 1 issue with the 'Task' type per week.

<div align="center">

| Specification |                                   |
| :------------ | :-------------------------------- |
| **Guarantee** | `NUMBER_DONEISSUES_WEEKLY_OVER_1` |
| **Scope**     | Member                            |
| **Period**    | Weekly                            |

</div>

### Application steps

1. An issue with the "Task" type is moved to the “Done" column.

<div align="center">

|           Objective           |
| :---------------------------: |
| `COUNT_DONEISSUES_MEMBER ≥ 1` |

</div>

**Where:**

- **COUNT_DONEISSUES_MEMBER**: Number of "Done" issues with the "Task" type by member in the last week.

### Workflow example

1. The member Paul has not put any issues with the "Task" type into the “Done” column this week yet. So he must finish an issue with the "Task" type before the weekends in order to comply with the established team practice.
2. Paul has a pull request approved by his team, so he proceeds to move the issue with the "Task" type related to that pull request from the “In Review” column to the “Done” column, thus complying with the team practice.

### Evaluation example

If Paul completed **2** "Done" issues with the "Task" type this week, the value is 2. Since $2 \ge 1$, compliance is satisfied.

---

# **TPg: Percentage of approved merged PR (by Team, Weekly)**

> **Rule:** Each Pull Request should be approved before merging.

<div align="center">

| Specification |                                                                     |
| :------------ | :------------------------------------------------------------------ |
| **Guarantee** | `CORRELATION_APPROVEDMERGEDPULLREQUEST_TOTALMERGEDPULLREQUEST_TEAM` |
| **Scope**     | Team                                                                |
| **Period**    | Weekly                                                              |

</div>

### Application steps

1. A pull request is created by a member.
2. A different member reviews the pull request with an approval review.
3. The pull request is merged.

<div align="center">

|                                   Objective                                    |
| :----------------------------------------------------------------------------: |
| `COUNT_MERGED_PR_WITH_POSITIVE_REVIEWS_TEAM / COUNT_PR_MERGED_TEAM × 100 ≥ 75` |

</div>

**Where:**

- **COUNT_MERGED_PR_WITH_POSITIVE_REVIEWS_TEAM**: Number of merged pull requests with at least one positive review by the team in the last week.
- **COUNT_PR_MERGED_TEAM**: Number of merged pull requests by the team in the last week.

### Workflow example

1. John creates a new pull request.
2. Elon reviews the pull request and approves it.
3. The pull request can now be merged.

### Evaluation example

If the team has **8** merged pull requests this week and **6** of them have at least one approved review:

<div align="center">

$\displaystyle \text{Value} = \left(\frac{6}{8}\right) \times 100 = 75$%

</div>

Since 75% ≥ 75%, compliance is satisfied.

---

# **TPh.1: Percentage of approved merged PR (by Member, Weekly)**

> **Rule:** Each developer should only merge a Pull Request if it is approved by his teammates.

<div align="center">

| Specification |                                                                       |
| :------------ | :-------------------------------------------------------------------- |
| **Guarantee** | `CORRELATION_APPROVEDMERGEDPULLREQUEST_TOTALMERGEDPULLREQUEST_MEMBER` |
| **Scope**     | Member                                                                |
| **Period**    | Weekly                                                                |

</div>

### Application steps

1. A pull request is created by a member.
2. A different member reviews the pull request with an approval review.
3. The pull request is merged.

<div align="center">

|                                     Objective                                      |
| :--------------------------------------------------------------------------------: |
| `COUNT_MERGED_PR_WITH_POSITIVE_REVIEWS_MEMBER / COUNT_PR_MERGED_MEMBER × 100 ≥ 75` |

</div>

**Where:**

- **COUNT_MERGED_PR_WITH_POSITIVE_REVIEWS_MEMBER**: Number of merged pull requests by member with at least one positive review during the last week.
- **COUNT_PR_MERGED_MEMBER**: Number of merged pull requests by the same member during the last week.

### Workflow example

1. John creates a new pull request.
2. Elon reviews the pull request and approves it.
3. The pull request can now be merged.

### Evaluation example

If John merged **4** pull requests this week and **3** of them had approved reviews:

<div align="center">

$\displaystyle \text{Value} = \left(\frac{3}{4}\right) \times 100 = 75$%

</div>

Since 75% ≥ 75%, compliance is satisfied.

---

# **TPh.2: Number of approved merged PR (By Member, Weekly)**

> **Rule:** Each developer must merge at least one pull request approved by his teammates per week.

<div align="center">

| Specification |                                           |
| :------------ | :---------------------------------------- |
| **Guarantee** | `NUMBER_APPROVEDMERGEDPULLREQUEST_MEMBER` |
| **Scope**     | Member                                    |
| **Period**    | Weekly                                    |

</div>

### Application steps

1. A pull request is created by a member.
2. A different member reviews the pull request with an approval review.
3. The pull request is merged.

<div align="center">

|                     Objective                      |
| :------------------------------------------------: |
| `COUNT_MERGED_PR_WITH_POSITIVE_REVIEWS_MEMBER ≥ 1` |

</div>

**Where:**

- **COUNT_MERGED_PR_WITH_POSITIVE_REVIEWS_MEMBER**: Number of merged pull requests by member with at least one positive review during the last week.

### Workflow example

1. John creates a new pull request.
2. Elon reviews the pull request and approves it.
3. The pull request can now be merged.

### Evaluation example

If John merged **3** pull requests this week and **2** of them had approved reviews, the value is **2**. Since $2 \ge 1$, compliance is satisfied.
