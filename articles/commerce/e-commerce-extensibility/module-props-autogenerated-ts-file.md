---
# required metadata

title: Module props.autogenerated.ts file
description: This topic provides information about the props.autogenerated.ts file for a module. This file is an automatically generated TypeScript file. It shouldn't be manually changed.
author: samjarawan
ms.date: 10/20/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Module props.autogenerated.ts file

[!include [banner](../includes/banner.md)]

## Overview

The props.autogenerated.ts file is a TypeScript file that is automatically generated for a module. It shouldn't be manually changed. If new configuration values are added to the module definition file and module data files, this file is automatically built so that it includes the appropriate interfaces.

## Example

The following example shows the props.autogenerated.ts file for a module.

```typescript
/**
 * Copyright (c) 2018 Microsoft Corporation
 * IProductFeature contentModule Interface Properties
 * THIS FILE IS AUTO-GENERATED - MANUAL MODIFICATIONS WILL BE LOST
 */

import * as Msdyn365 from '@msdyn365-commerce/core';

export const enum imageAlignment {
    left = 'left',
    right = 'right'
}

export interface IProductFeatureConfig extends Msdyn365.IModuleConfig {
    imageAlignment?: imageAlignment;
    productTitle?: string;
    productDetails?: Msdyn365.RichText;
    productImage?: Msdyn365.IImageData;
    buttonText?: string;
    productIds?: string;
}

export interface IProductFeatureResources {
    resourceKey: string;
}

export interface IProductFeatureProps<T> extends Msdyn365.IModule<T> {
    resources: IProductFeatureResources;
    config: IProductFeatureConfig;
}
```

## Additional resources

[Modules overview](modules-overview.md)

[Module definition file](module-definition-file.md)

[Module React component file](module-react-file.md)

[Module view file](module-view-file.md)

[Module data file](module-data-file.md)

[Module mock file](module-mock-file.md)

[Module test file](module-test-file.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]