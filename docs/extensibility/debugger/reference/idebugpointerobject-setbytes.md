---
title: IDebugPointerObject::SetBytes | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1e7b3fd72285f6a6c9c4abeca4e6b262d981be8f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331553"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Ustawia wartość wskazywana z szeregu kolejnych bajtów.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int SetBytes(
   uint     dwStart,
   uint     dwCount,
   byte[]   pBytes,
   out uint pdwBytes
);
```

## <a name="parameters"></a>Parametry
`dwStart`\
[in] Przesunięcie w bajtach od początku, jaki wskazał obiekt.

`dwCount`\
[in] Liczba bajtów do zestawu.

`pBytes`\
[in] Tablica bajtów reprezentujący nową wartość. Ta wartość jest przechowywana do obiektu, rozpoczynając od danego przesunięcia.

`pdwBytes`\
[out] Zwraca liczbę bajtów faktycznie zestawu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest używana, jeśli wskaźnik, reprezentowane przez to [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) wskazuje typ pierwotny lub prostej tablicy typów pierwotnych (czyli tablicę, która może być reprezentowany za pomocą prostych sekwencji bajtów). To `IDebugPointerObject` obiekt nie może być odwołaniem do wartości null (go musi wskazywać adres w pamięci).

## <a name="see-also"></a>Zobacz także
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)