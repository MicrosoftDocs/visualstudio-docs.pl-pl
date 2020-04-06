---
title: IDebugField::GetExtendedInfo | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetExtendedInfo
helpviewer_keywords:
- IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dc414dd57e86149e38d7c85d11252eb93efced51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728873"
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Ta metoda pobiera rozszerzone informacje o polu.

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
[w] Wybiera informacje, które mają zostać zwrócone. Prawidłowe wartości:

|Wartość|Opis|
|-----------|-----------------|
|`guidConstantValue`|Wartość jako sekwencja bajtów.|
|`guidConstantType`|Typ jako podpis typu.|

`prgBuffer`\
[na zewnątrz] Zwraca informacje rozszerzone.

`pdwLen`\
[w, na zewnątrz] Zwraca rozmiar informacji rozszerzonych w bajtach.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Obecnie ta metoda zwraca tylko typ lub wartość stałej. Wywołujący musi zwolnić bufor `prgBuffer` zwrócony przez `CoTaskMemFree` wywołanie funkcji COM <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C++) lub (C#).

## <a name="see-also"></a>Zobacz też
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
