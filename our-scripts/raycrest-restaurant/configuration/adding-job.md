---
description: >-
  This page contains the job configuration you need to add to your server.
  Download the file or copy the code from the tab that matches your framework
  and add it to the correct location.
---

# Adding Job

{% tabs %}
{% tab title="QBCore" %}
Add the following job to your <mark style="color:yellow;">`qb-core/shared/jobs.lua`</mark> file:

```lua
raycrest = {
    label = 'Raycrest Restaurant',
    type = 'restaurant',
    defaultDuty = false,
    offDutyPay = false,
    grades = {
        ['0'] = { name = 'Waiter', payment = 50 },
        ['1'] = { name = 'Cook', payment = 75 },
        ['2'] = { name = 'Chef', payment = 100 },
        ['3'] = { name = 'Head Chef', payment = 125 },
        ['4'] = { name = 'Assistant Manager', payment = 150 },
        ['5'] = { name = 'Manager', isboss = true, payment = 175 },
        ['6'] = { name = 'Owner', isboss = true, payment = 200 },
    },
},
```
{% endtab %}

{% tab title="QBOX" %}
Add the following job to your <mark style="color:yellow;">`qbx_core/shared/jobs.lua`</mark> file:

```lua
raycrest = {
    label = 'Raycrest Restaurant',
    type = 'restaurant',
    defaultDuty = false,
    offDutyPay = false,
    grades = {
        [0] = { name = 'Waiter', payment = 50 },
        [1] = { name = 'Cook', payment = 75 },
        [2] = { name = 'Chef', payment = 100 },
        [3] = { name = 'Head Chef', payment = 125 },
        [4] = { name = 'Assistant Manager', payment = 150 },
        [5] = { name = 'Manager', isboss = true, payment = 175},
        [6] = { name = 'Owner', isboss = true, bankAuth = true, payment = 200 },
    },
},
```
{% endtab %}

{% tab title="ESX" %}
Download the SQL file below and import it into your ESX database. This will add the job and all job grades.

{% file src="../../../.gitbook/assets/esx_job_setup.sql" %}

***

#### Alternative Method (Optional)

{% hint style="info" %}
If you already imported the SQL file, you can ignore this. If you prefer to copy-paste the queries directly, use the code below.
{% endhint %}

```sql
-- Insert the job
INSERT INTO `jobs` (`name`, `label`) VALUES ('raycrest', 'Raycrest Restaurant');

-- Insert job grades
INSERT INTO `job_grades` (`job_name`, `grade`, `name`, `label`, `salary`, `skin_male`, `skin_female`) VALUES
('raycrest', 0, 'waiter', 'Waiter', 50, '{}', '{}'),
('raycrest', 1, 'cook', 'Cook', 75, '{}', '{}'),
('raycrest', 2, 'chef', 'Chef', 100, '{}', '{}'),
('raycrest', 3, 'head_chef', 'Head Chef', 125, '{}', '{}'),
('raycrest', 4, 'assistant_manager', 'Assistant Manager', 150, '{}', '{}'),
('raycrest', 5, 'boss', 'Manager', 175, '{}', '{}'),
('raycrest', 6, 'boss', 'Owner', 200, '{}', '{}');
```
{% endtab %}
{% endtabs %}
