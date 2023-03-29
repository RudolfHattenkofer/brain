```
insert into company_value_revisions
select uuid_generate_v4() as id, id as company_value_id, now(), false as flagged_for_review, comment as review_comment, exists, value, document_id, document_ref, material, material_reason, 'system' as created_by, own_calculation from company_values
```

