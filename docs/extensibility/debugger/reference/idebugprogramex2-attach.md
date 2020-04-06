---
title: IDebugProgramEx2::Dołącz | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fcb52a96074b783043af1e908cf454466df74c30
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722381"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Dołącz sesję do programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason,
   IDebugSession2*       pSession
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   uint                 dwReason,
   IDebugSession2       pSession
);
```

## <a name="parameters"></a>Parametry
`pCallback`\
[w] [Obiekt IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) który reprezentuje funkcję wywołania zwrotnego, do których dołączony jest aparat debugowania wysyła zdarzenia.

`dwReason`\
[w] Wartość z [wyliczenia ATTACH_REASON,](../../../extensibility/debugger/reference/attach-reason.md) która opisuje przyczynę operacji dołączania.

`pSession`\
[w] Wartość, która jednoznacznie identyfikuje sesję, która jest dołączana do programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu. Ta metoda `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` powinna zostać wrócona, jeśli program jest już dołączony.

## <a name="remarks"></a>Uwagi
 Port zawierający program może użyć `pSession` tej wartości do określenia, która sesja próbuje dołączyć do programu. Na przykład jeśli port umożliwia dołączanie tylko jednej sesji debugowania do procesu w czasie, port może określić, czy ta sama sesja jest już dołączona do innych programów w procesie.

> [!NOTE]
> Interfejs przekazywany `pSession` jest traktowany tylko jako plik cookie, wartość, która jednoznacznie identyfikuje menedżera debugowania sesji dołączającego do tego programu; żadna z metod na dostarczonym interfejsie nie jest funkcjonalna.

## <a name="see-also"></a>Zobacz też
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
