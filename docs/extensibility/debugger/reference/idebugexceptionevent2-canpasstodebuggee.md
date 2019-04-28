---
title: IDebugExceptionEvent2::CanPassToDebuggee | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93652efe19096466c853d758cc36aa022236068d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920093"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Określa, czy aparat debugowania (DE) obsługuje możliwość przekazywania ten wyjątek do debugowanego po wznowieniu działania wykonywania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Wartość zwracana
 Zwraca albo `S_OK` (wyjątek może być przekazywany do program) lub `S_FALSE` (wyjątek nie mogą być przekazywane).

## <a name="remarks"></a>Uwagi
 DE musi mieć domyślnej akcji do przekazania do debugowany program. IDE może zostać wyświetlony [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) zdarzenia i wywołania [Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md) metody bez wywoływania `CanPassToDebuggee` metody. W związku z tym DE powinien mieć przypadek domyślny, przekazywania wyjątek, czy nie.

## <a name="see-also"></a>Zobacz też
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)