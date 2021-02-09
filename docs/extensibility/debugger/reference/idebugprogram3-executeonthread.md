---
title: 'IDebugProgram3:: ExecuteOnThread | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8df69c02fb7e78dbb107db906de59d8b7e5881b4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887071"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Wykonuje program debugera. Wątek jest zwracany w celu udostępnienia informacji debugera, na których wątku użytkownik przegląda podczas wykonywania programu.

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
podczas Obiekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) .

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Istnieją trzy różne sposoby, aby debuger mógł wznowić wykonywanie po zatrzymywaniu:

- Wykonaj: anuluje wszystkie poprzednie kroki i uruchamiaj do następnego punktu przerwania i tak dalej.

- Krok: Anuluj dowolny stary krok i uruchom do momentu zakończenia nowego kroku.

- Kontynuuj: ponownie uruchom i pozostaw wszystkie starsze, aktywne.

  Wątek przeszedł do `ExecuteOnThread` jest przydatny podczas wybierania kroku do anulowania. Jeśli nie znasz wątku, uruchomienie polecenie Execute powoduje anulowanie wszystkich kroków. Mając wiedzę na temat wątku, wystarczy anulować krok w aktywnym wątku.

## <a name="see-also"></a>Zobacz też
- [Wykonaj polecenie](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
