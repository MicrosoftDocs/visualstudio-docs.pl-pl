---
title: IDebugPointerObject::SetBytes | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e54a7f38eed85ffe2757b373de1af59e1aaa126b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694730"
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

#### <a name="parameters"></a>Parametry
 `dwStart`

 [in] Przesunięcie w bajtach od początku, jaki wskazał obiekt.

 `dwCount`

 [in] Liczba bajtów do zestawu.

 `pBytes`

 [in] Tablica bajtów reprezentujący nową wartość. Ta wartość jest przechowywana do obiektu, rozpoczynając od danego przesunięcia.

 `pdwBytes`

 [out] Zwraca liczbę bajtów faktycznie zestawu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest używana, jeśli wskaźnik, reprezentowane przez to [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) wskazuje typ pierwotny lub prostej tablicy typów pierwotnych (czyli tablicę, która może być reprezentowany za pomocą prostych sekwencji bajtów). To `IDebugPointerObject` obiekt nie może być odwołaniem do wartości null (go musi wskazywać adres w pamięci).

## <a name="see-also"></a>Zobacz też
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)