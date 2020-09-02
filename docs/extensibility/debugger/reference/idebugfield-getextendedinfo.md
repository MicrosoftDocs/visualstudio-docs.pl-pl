---
title: 'IDebugField:: GetExtendedInfo | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
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
podczas Wybiera informacje do zwrócenia. Prawidłowe wartości:

|Wartość|Opis|
|-----------|-----------------|
|`guidConstantValue`|Wartość jako sekwencja bajtów.|
|`guidConstantType`|Typ jako sygnatura typu.|

`prgBuffer`\
określoną Zwraca informacje rozszerzone.

`pdwLen`\
[in. out] Zwraca rozmiar rozszerzonych informacji w bajtach.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Obecnie ta metoda zwraca tylko typ lub wartość stałej. Obiekt wywołujący musi zwolnić bufor zwrócony `prgBuffer` przez wywołanie `CoTaskMemFree` funkcji com (C++) lub <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).

## <a name="see-also"></a>Zobacz też
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
