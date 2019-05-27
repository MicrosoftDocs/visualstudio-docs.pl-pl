---
title: IDebugMethodField::IsCustomAttributeDefined | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0dfbe855f5bdcbfda384e7a9a180fc8f86595b85
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211934"
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
Określa, czy zdefiniowano określonego atrybutu niestandardowego.

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
 Zwraca wartość S_OK, jeśli atrybut niestandardowy jest zdefiniowane w tej metodzie, w przeciwnym razie zwraca S_FALSE.

## <a name="see-also"></a>Zobacz także
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)