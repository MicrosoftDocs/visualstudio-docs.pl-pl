---
description: Pobiera wartość wskazywaną przez serię kolejnych bajtów.
title: 'IDebugPointerObject:: GetBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a150f819610de97ee292302d89e2007c6235aae
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087629"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Pobiera wartość wskazywaną przez serię kolejnych bajtów.

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
podczas Przesunięcie w bajtach od początku obiektu wskazywanego przez.

`dwCount`\
podczas Liczba bajtów do pobrania.

`pBytes`\
[in. out] Tablica, która jest wypełniana wartością jako seria kolejnych bajtów, rozpoczynając od danego przesunięcia od obiektu wskazywanego przez.

`pdwBytes`\
określoną Zwraca liczbę bajtów pobieranych w rzeczywistości.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest używana, jeśli wskaźnik reprezentowany przez ten [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) wskazuje na typ pierwotny lub prostą tablicę typów pierwotnych (czyli tablicę, która może być reprezentowana przez prostą sekwencję bajtów).

## <a name="see-also"></a>Zobacz też
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
