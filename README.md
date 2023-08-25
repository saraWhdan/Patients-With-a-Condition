# Patients-With-a-Condition


Problem Link: https://leetcode.com/problems/patients-with-a-condition/description/?envType=study-plan-v2&envId=top-sql-50

## Solution
- With join 
```sql
select p.patient_id,p.patient_name ,p.conditions
from Patients p
inner join (SELECT  patient_id, value 
FROM Patients 
cross apply string_split(conditions,' ')
WHERE value LIKE 'DIAB1%') c on c.patient_id=p.patient_id

```
- Without join (more simple one)
  ```sql
  select * from Patients
  where conditions like 'DIAB1%' OR conditions like  '% DIAB1%'

