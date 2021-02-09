---
title: 'IDebugProgram2:: terminate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a186bd39dab7ab1f7228504070f50b3aa6c311
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911896"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Kończy program.

## <a name="syntax"></a>Składnia

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli to możliwe, program zostanie zakończony i zwolniony z procesu; w przeciwnym razie aparat debugowania (DE) wykona niezbędne czyszczenie.

 Ta metoda lub metoda [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) jest wywoływana przez IDE, zazwyczaj w odpowiedzi na użytkownika, który zatrzymuje wszystkie debugowanie. Implementacja tej metody powinna, najlepiej zakończyć działanie programu w ramach procesu. Jeśli nie jest to możliwe, należy zapobiegać uruchamianiu przez program więcej w tym procesie (i wykonać wszelkie niezbędne czyszczenie). Jeśli `IDebugProcess2::Terminate` Metoda została wywołana przez IDE, cały proces zostanie zakończony jakiś czas po `IDebugProgram2::Terminate` wywołaniu metody.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Zakończ](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)
