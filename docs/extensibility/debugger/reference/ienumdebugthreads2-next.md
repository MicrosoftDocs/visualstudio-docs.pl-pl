---
title: 'IEnumDebugThreads2:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Next
helpviewer_keywords:
- IEnumDebugThreads2::Next
ms.assetid: bcffd954-3c67-4867-96f3-041ddb3e34d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc6c493c211da3dc69e25b20c0a79b4dcabd1ed6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715166"
---
# <a name="ienumdebugthreads2next"></a>IEnumDebugThreads2::Next
Zwraca następny zestaw elementów z wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Next(
   ULONG           celt,
   IDebugThread2** rgelt,
   ULONG*          pceltFetched
);
```

```csharp
int Next(
   uint            celt,
   IDebugThread2[] rgelt,
   ref uint        pceltFetched
);
```

## <a name="parameters"></a>Parametry
`celt`\
podczas Liczba elementów do pobrania. Określa również maksymalny rozmiar `rgelt` tablicy.

`rgelt`\
[in. out] Tablica elementów [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) do wypełnienia.

`pceltFetched`\
określoną Zwraca liczbę elementów faktycznie zwracanych w elemencie `rgelt` .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość `S_FALSE` , jeśli nie można zwrócić wymaganej liczby elementów; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
