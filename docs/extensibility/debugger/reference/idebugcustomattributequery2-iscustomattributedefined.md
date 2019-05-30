---
title: IDebugCustomAttributeQuery2::IsCustomAttributeDefined | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e2ecd70eeeddb4b61d8ed8d307bd579c68ef519
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335823"
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
[in] Ciąg zawierający nazwę atrybutu niestandardowego można znaleźć.

## <a name="return-value"></a>Wartość zwracana
 Zwraca wartość S_OK, jeśli atrybut niestandardowy jest zdefiniowany w tym polu, w przeciwnym razie zwraca S_FALSE.

## <a name="remarks"></a>Uwagi
 Aby uzyskać bajtów atrybut skojarzony z atrybutu niestandardowego, należy wywołać [getcustomattributebyname —](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) metody.

## <a name="see-also"></a>Zobacz także
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)