---
id: 5d1093c0-c427-4f73-99bc-4d93fe865e82
title: Unix
desc: ''
updated: 1614537039729
created: 1607463112448
---

### Quick per line processing

e.g. clean up S3 buckets 

```
while read -r line ; do; echo $line; aws s3 rm s3://$line --recursive && aws s3 rb s3://$line ; done
```