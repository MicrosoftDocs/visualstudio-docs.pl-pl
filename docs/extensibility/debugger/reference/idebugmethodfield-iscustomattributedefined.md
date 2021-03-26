---
description: Określa, czy określony atrybut niestandardowy został zdefiniowany.
title: 'IDebugMethodField:: IsCustomAttributeDefined | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7cd9e1ae31e893639b41537bb5b09323cc70ff9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081896"
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
Określa, czy określony atrybut niestandardowy został zdefiniowany.

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
 Zwraca S_OK, jeśli atrybut niestandardowy jest zdefiniowany w tej metodzie, w przeciwnym razie zwraca S_FALSE.

## <a name="see-also"></a>Zobacz też
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
