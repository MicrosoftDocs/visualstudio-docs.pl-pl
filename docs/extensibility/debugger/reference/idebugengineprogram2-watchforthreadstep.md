---
title: IDebugEngineProgram2::WatchForThreadStep | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf0474d527b7c6f1d180201a463f52a0b17d18fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730352"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Zegarki do wykonania (lub zatrzymuje oglądania do wykonania) występuje na danym wątku.

## <a name="syntax"></a>Składnia

```cpp
HRESULT WatchForThreadStep( 
   IDebugProgram2* pOriginatingProgram,
   DWORD           dwTid,
   BOOL            fWatch,
   DWORD           dwFrame
);
```

```csharp
int WatchForThreadStep( 
   IDebugProgram2 pOriginatingProgram,
   uint           dwTid,
   int            fWatch,
   uint           dwFrame
);
```

## <a name="parameters"></a>Parametry
`pOriginatingProgram`\
[w] Obiekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) reprezentujący program jest stopniowany.

`dwTid`\
[w] Określa identyfikator wątku do obejrzenia.

`fWatch`\
[w] Non-zero`TRUE`( ) oznacza rozpoczęcie obserwacji wykonania `dwTid`na wątku zidentyfikowanym przez ; w przeciwnym`FALSE`razie zero ( ) `dwTid`oznacza zatrzymanie oglądania do wykonania na .

`dwFrame`\
[w] Określa indeks ramki sterujący typem kroku. Gdy jest to wartość wynosi zero (0), typ kroku jest "krok do" i `dwTid` program powinien zatrzymać, gdy wątek zidentyfikowany przez wykonuje. Gdy `dwFrame` nie ma zera, typ kroku jest "krok po kroku" i program `dwTid` powinien zatrzymać się tylko wtedy, gdy wątek identyfikowany przez jest uruchomiony w ramce, której indeks jest równy lub wyższy na stosie niż `dwFrame`.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Gdy menedżer debugowania sesji (SDM) kroki programu, identyfikowane przez `pOriginatingProgram` parametr, powiadamia wszystkie inne dołączone programy, wywołując tę metodę.

 Ta metoda ma zastosowanie tylko do stepping tego samego wątku.

## <a name="see-also"></a>Zobacz też
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
