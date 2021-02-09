---
title: 'IDebugArrayObject:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9750b2982ad0b2d70375fe0519a9fd888bcac8a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870223"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Pobiera liczbę elementów w tablicy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetCount( 
   DWORD* pdwElements
);
```

```csharp
int GetCount(
   out uint pdwElements
);
```

## <a name="parameters"></a>Parametry
`pdwElements`\
określoną Zwraca liczbę.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda widzi wszystkie elementy obiektu Array jako tablicę jednowymiarową, nawet jeśli obiekt Array jest wielowymiarowych. Na przykład, dana tablica `myarray[3][2][6]` , ta metoda zwróci wartość 36 w `pdwElements` parametrze. Użyj metody [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) , aby pobrać pojedyncze elementy pojedynczo.

## <a name="see-also"></a>Zobacz też
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
