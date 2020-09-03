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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9d5e322b7bcd5238335c74caa21989f1f1962ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736198"
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
