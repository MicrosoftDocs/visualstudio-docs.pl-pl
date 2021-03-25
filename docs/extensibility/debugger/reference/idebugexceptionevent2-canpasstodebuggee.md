---
description: Określa, czy aparat debugowania (DE) obsługuje opcję przekazywania tego wyjątku do debugowanego programu podczas wznawiania wykonywania.
title: 'IDebugExceptionEvent2:: CanPassToDebuggee | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7fbc5cd55516f018a0a0877a114169a436b97fe1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084847"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Określa, czy aparat debugowania (DE) obsługuje opcję przekazywania tego wyjątku do debugowanego programu podczas wznawiania wykonywania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Wartość zwracana
 Zwraca albo `S_OK` (wyjątek można przesłać do programu) lub `S_FALSE` (nie można przesłać wyjątku).

## <a name="remarks"></a>Uwagi
 Element DE musi mieć domyślną akcję do przekazania do debugowanego obiektu. IDE może odebrać zdarzenie [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) i wywołać metodę [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) bez wywoływania `CanPassToDebuggee` metody. W związku z tym, DE powinien mieć domyślny przypadek do przekazania wyjątku w lub nie.

## <a name="see-also"></a>Zobacz też
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Kontynuuj](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
