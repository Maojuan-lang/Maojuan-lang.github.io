---
title: yaml的横杠
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

