---
title: yaml的横杠
date: 2024-08-03
---

```
requests:
  - method: 
        GET
    path:
        - '{{fBaseURL}}'
        - '{{fBaseURL}}'
        
{
  "requests": [
    {
      "path": [
        "{{fBaseURL}}", 
        "{{fBaseURL}}"
      ], 
      "method": "GET"
    }
  ]
}
```

```
requests:
  - method: 
        GET
  - path:
        - '{{fBaseURL}}'
        - '{{fBaseURL}}'
        
        
{
  "requests": [
    {
      "method": "GET"
    }, 
    {
      "path": [
        "{{fBaseURL}}", 
        "{{fBaseURL}}"
      ]
    }
  ]
}
```

