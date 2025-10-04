--JOIN is to combine tables, and this will not take null data
--When we combine tables with JOIN, we can use alias to name different tables, so we can easily read them.
--Inner JOIN: Only records that exist in both tables
--Left JOIN: All records in the left table; even if they do NOT have a matching to the right table
--Right JOIN: All records in the right table; even if they do NOT have a matching to the left table
--Full outer JOIN: All records in the right table;even if they do NOT have a matching to the left table
--We use "CASE WHEN" to state "if...else..."
--EX: CASE WHEN pri_dx_icd = 'I10' OR sec_dx_icd = 'I10' THEN 1 ELSE 0 END AS HTN
--COUNT(*): count all
--COUNT(DISTINCT): count the value of specific column
--GROUP BY: to group the data by specific column
--GROUP BY is usually used with SUM, AVG, COUNT, MAX, and MIN


--Below is the approach that An and I organized during our discussion.
select v.attending_md AS Provider, --select provider name using visit table
count(DISTINCT v.visit_id) as N_visits, -- count unique visit id from visit table
COUNT(DISTINCT m.Rx_name || m.Pid || m.Rx_date) as Drug_count, -- count the unique combination of rx_name + pid + rx_date (drug name + patient id + date)
COUNT(DISTINCT l.Lab_loinc || l.Pid || l.Lab_date) as Lab_count -- count the unique combination of lab_loinc + p_id + lab_date ( lab name + patient id + lab date)
FROM VISIT v
FULL OUTER JOIN MEDICATIONS m ON v.Attending_md = m.Prescribing_md -- join the medication table with visit table (left join did not change the result)
FULL OUTER JOIN LABS l ON v.Attending_md = l.Ordering_md -- join the labs table with visit table (left join did not change the result)
GROUP BY Provider; -- group by provider name
