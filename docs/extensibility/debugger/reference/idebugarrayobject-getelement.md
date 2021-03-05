---
description: Pobiera element tablicy.
title: 'IDebugArrayObject:: GetElement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea10afac9f5503288d257833d6dd59f9ba56fc6f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158660"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
Pobiera element tablicy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetElement( 
   DWORD          dwIndex,
   IDebugObject** ppElement
);
```

```csharp
int GetElement(
   [In] uint dwIndex,
   out IDebugObject ppElement
);
```

## <a name="parameters"></a>Parametry
`dwIndex`\
podczas Indeks elementu.

`ppElement`\
określoną Zwraca interfejs [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , który reprezentuje element.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda widzi wszystkie elementy obiektu Array jako tablicę jednowymiarową, nawet jeśli obiekt Array jest wielowymiarowych. Na przykład, dana tablica `myarray[3][2][6]` i `dwIndex` parametr 20, ta metoda zwróci element z `myarray[1][1][2]` , a `dwIndex` parametr 21 zwróci element z `myarray[1][1][3]` . Użyj metody [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) , aby określić łączną liczbę elementów w tablicy.

## <a name="see-also"></a>Zobacz też
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
