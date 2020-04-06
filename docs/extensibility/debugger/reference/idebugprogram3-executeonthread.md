---
title: IDebugProgram3::ExecuteOnThread | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 201c08352bc5b616298349c52197529ef3f1a7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722662"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Wykonuje program debugera. Wątek jest zwracany, aby dać debugerowi informacje o tym, który wątek jest przeglądany przez użytkownika podczas wykonywania programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT ExecuteOnThread(
   [in] IDebugThread2* pThread)
```

```csharp
int ExecuteOnThread(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parametry
`pThread`\
[w] [Obiekt IDebugThread2.](../../../extensibility/debugger/reference/idebugthread2.md)

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Istnieją trzy różne sposoby, które debuger można wznowić wykonywanie po zatrzymaniu:

- Wykonaj: Anuluj dowolny poprzedni krok i uruchom do następnego punktu przerwania i tak dalej.

- Krok: Anuluj dowolny stary krok i uruchom do momentu ukończenia nowego kroku.

- Kontynuuj: Uruchom ponownie i pozostaw dowolny stary krok aktywny.

  Wątek `ExecuteOnThread` przekazany do jest przydatne przy podejmowaniu decyzji, który krok do anulowania. Jeśli nie znasz wątku, uruchomienie execute anuluje wszystkie kroki. Znając wątek, wystarczy anulować krok w aktywnym wątku.

## <a name="see-also"></a>Zobacz też
- [Realizacja](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
