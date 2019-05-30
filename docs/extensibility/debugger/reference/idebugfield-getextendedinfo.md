---
title: IDebugField::GetExtendedInfo | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3ddae4ea7ecc58d67279ae638d19bf95ec2cc591
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352655"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Ta metoda pobiera rozszerzone informacje dotyczące pola.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetExtendedInfo( 
   REFGUID guidExtendedInfo,
   BYTE**  prgBuffer,
   DWORD*  pdwLen
);
```

```csharp
int GetExtendedInfo(
   ref Guid guidExtendedInfo,
   IntPtr[] prgBuffer,
   ref uint pdwLen
);
```

## <a name="parameters"></a>Parametry
`guidExtendedInfo`\
[in] Wybiera informacje, które mają zostać zwrócone. Prawidłowe wartości to:

|Wartość|Opis|
|-----------|-----------------|
|`guidConstantValue`|Wartość atrybutu jako sekwencja bajtów.|
|`guidConstantType`|Typ jako typ podpisu.|

`prgBuffer`\
[out] Zwraca informacje o rozszerzonych.

`pdwLen`\
[out w] Zwraca rozmiar rozszerzone informacje w bajtach.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Obecnie metoda ta zwraca tylko typ lub wartość stałą. Obiekt wywołujący należy zwolnić buforu zwracane w `prgBuffer` przez wywołanie modelu COM `CoTaskMemFree` — funkcja (C++) lub <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).

## <a name="see-also"></a>Zobacz także
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)