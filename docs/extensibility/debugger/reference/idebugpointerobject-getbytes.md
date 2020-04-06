---
title: IDebugPointerObject::GetBytes | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 17bc39f65d7c4c42b4f958b559df7c5b7d3bbdf7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725516"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Pobiera wartość wskazywał jako serię kolejnych bajtów.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int GetBytes(
   uint       dwStart,
   uint       dwCount,
   out byte[] pBytes,
   out uint   pdwBytes
);
```

## <a name="parameters"></a>Parametry
`dwStart`\
[w] Przesunięcie w bajtach od początku obiektu wskazywowane.

`dwCount`\
[w] Liczba bajtów do pobrania.

`pBytes`\
[w, na zewnątrz] Tablica, która jest wypełniona wartością jako seria kolejnych bajtów, zaczynając od danego odsunięcia od obiektu wskazywała.

`pdwBytes`\
[na zewnątrz] Zwraca liczbę bajtów faktycznie pobranych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest używana, jeśli wskaźnik reprezentowany przez ten [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) wskazuje na typ pierwotny lub prostą tablicę typów pierwotnych (czyli tablicę, która może być reprezentowana przez prostą sekwencję bajtów).

## <a name="see-also"></a>Zobacz też
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
