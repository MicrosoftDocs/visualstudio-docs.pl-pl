---
title: IDebugEngineProgram2::WatchForThreadStep | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5d144d02a34052cc06e5f63df75a2a7db3be4887
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984018"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Oczekuje na wykonanie (lub zatrzymuje oczekiwania na wykonanie) występuje dla danego wątku.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `pOriginatingProgram`  
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt reprezentujący ten program jest zmieniana.  
  
 `dwTid`  
 [in] Określa identyfikator wątku, aby obejrzeć.  
  
 `fWatch`  
 [in] Niezerowa Koniunkcja (`TRUE`) oznacza start oczekiwania na wykonanie na wątku identyfikowane przez `dwTid`; w przeciwnym razie wartość zero (`FALSE`) oznacza, że zatrzymanie, oczekiwania na wykonanie na `dwTid`.  
  
 `dwFrame`  
 [in] Określa indeks ramki, który określa typ kroku. Jeśli jest to wartość zero (0), typ kroku jest "wkroczyć do" i program powinna zostać przerwana w każdym przypadku, gdy wątek jest identyfikowane za pomocą `dwTid` wykonuje. Gdy `dwFrame` jest różna od zera, typ kroku jest "Przekrocz nad" i program ma zostać zatrzymana, tylko wtedy, gdy wątek jest identyfikowane za pomocą `dwTid` działa w ramce, którego indeks to równą lub większą na stosie niż `dwFrame`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Gdy Menedżer debugowania sesji (SDM) kroki programu identyfikowane przez `pOriginatingProgram` parametru, powiadomi użytkownika wszystkie inne programy dołączone przez wywołanie tej metody.  
  
 Ta metoda ma zastosowanie tylko do tego samego wątku przechodzenie krok po kroku.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)