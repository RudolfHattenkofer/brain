Create revisions:
```
insert into company_value_revisions
select uuid_generate_v4() as id, id as company_value_id, now(), false as flagged_for_review, comment as review_comment, exists, value, document_id, document_ref, material, material_reason, 'system' as created_by, own_calculation from company_values
```

Then verify:
```
update company_values
set verified_at = now(), verified_by = 'system', verified = true, verified_revision_id = company_value_revisions.id
from company_value_revisions
where company_value_revisions.company_value_id = company_values.id
```

```
update company_values
set company_id = documents.company_id
from documents
where company_values.document_id = documents.id
```