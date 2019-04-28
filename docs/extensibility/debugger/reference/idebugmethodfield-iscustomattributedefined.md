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
ms.openlocfilehash: 08534abc468ac358d7c5eeba25129d9752f84e5a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872832"
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

#### <a name="parameters"></a>Parametry
 `pszCustomAttributeName`

 [in] Ciąg zawierający nazwę atrybutu niestandardowego można znaleźć.

## <a name="return-value"></a>Wartość zwracana
 Zwraca wartość S_OK, jeśli atrybut niestandardowy jest zdefiniowane w tej metodzie, w przeciwnym razie zwraca S_FALSE.

## <a name="see-also"></a>Zobacz też
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)