---
description: Określa, czy atrybut niestandardowy istnieje według nazwy.
title: 'IDebugCustomAttributeQuery2:: IsCustomAttributeDefined | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 646fe46f9d83a320423136b8601ee56b3f4ac583
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077593"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
Określa, czy atrybut niestandardowy istnieje według nazwy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT IsCustomAttributeDefined( 
   LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
   [In] string pszCustomAttributeName
);
```

## <a name="parameters"></a>Parametry
`pszCustomAttributeName`\
podczas Ciąg zawierający nazwę atrybutu niestandardowego do znalezienia.

## <a name="return-value"></a>Wartość zwracana
 Zwraca S_OK, jeśli atrybut niestandardowy jest zdefiniowany w tym polu, w przeciwnym razie zwraca S_FALSE.

## <a name="remarks"></a>Uwagi
 Aby uzyskać atrybut bajty skojarzone z atrybutem niestandardowym, wywołaj metodę [GetCustomAttributeByName —](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
