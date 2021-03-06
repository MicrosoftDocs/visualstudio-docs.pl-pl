---
description: Określa, czy wyjątek powinien być przekazywać do debugowanego programu po wznowieniu wykonywania lub czy wyjątek powinien zostać odrzucony.
title: IDebugExceptionEvent2::P assToDebuggee | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f81af5686cfc2b99dc3bf5d95e2ec283933297e2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084769"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Określa, czy wyjątek powinien być przekazywać do debugowanego programu po wznowieniu wykonywania lub czy wyjątek powinien zostać odrzucony.

## <a name="syntax"></a>Składnia

```cpp
HRESULT PassToDebuggee(
   BOOL fPass
);
```

```csharp
int PassToDebuggee(
   int fPass
);
```

## <a name="parameters"></a>Parametry
`fPass`\
podczas Różna od zera ( `TRUE` ), jeśli wyjątek powinien zostać przesłany do debugowanego programu po wznowieniu wykonywania lub zero ( `FALSE` ), jeśli wyjątek powinien zostać odrzucony.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wywołanie tej metody nie powoduje faktycznego wykonania żadnego kodu w debugowanym programie. Wywołanie jest tylko ustawieniem stanu dla następnego wykonania kodu. Na przykład wywołania metody [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) mogą zwracać się `S_OK` z [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` pole ustawione na `EXCEPTION_STOP_SECOND_CHANCE` .

 IDE może odebrać zdarzenie [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) i wywołać metodę [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md) . Aparat debugowania (DE) powinien mieć domyślne zachowanie do obsługi przypadku, jeśli `PassToDebuggee` Metoda nie jest wywoływana.

## <a name="see-also"></a>Zobacz też
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Kontynuuj](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
