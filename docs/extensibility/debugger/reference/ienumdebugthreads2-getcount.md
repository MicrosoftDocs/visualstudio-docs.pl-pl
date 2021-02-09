---
title: 'IEnumDebugThreads2:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::GetCount
helpviewer_keywords:
- IEnumDebugThreads2::GetCount
ms.assetid: 81b7f139-d24e-4040-9adc-d664d77563ba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0ac9726874a34049c511616f63a7670035c5637a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852859"
---
# <a name="ienumdebugthreads2getcount"></a>IEnumDebugThreads2::GetCount
Zwraca liczbę elementów w wyliczeniu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetCount(
   ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parametry
`pcelt`\
określoną Zwraca liczbę elementów w wyliczeniu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda nie jest częścią niestandardowego interfejsu wyliczenia modelu COM, który określa, że należy `Next` `Clone` zaimplementować tylko metody,, `Skip` i `Reset` .

## <a name="see-also"></a>Zobacz też
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
