[https://create-react-app.dev/](https://create-react-app.dev/)

[TypeScript: Typed JavaScript at Any Scale.](https://www.typescriptlang.org/)

## Setup

```swift
npx create-react-app my-app --template typescript
```

Fix absolute import URLs:

```swift
# vi tsconfig.json
{
  "compilerOptions": {
    ...
    "baseUrl": "src"
  }
}
```

## Add new component

```swift
npx generate-react-cli component Whatever
```

## Run stuff once

```swift
import React, { useState, useEffect } from 'react';

const IndexPage: React.FC = (props) => {
  useEffect(() => {
    // Run code here
  }, [])

  return (
    <div className={styles.IndexPage}>
      Test
    </div>
  );
};
```

## Fetch data on init

```swift
useEffect(() => {
    const fetchData = async () => {
      const result = await fetchPartners();

      setPartnerList(result);
    }

    fetchData();
  }, []);
```



