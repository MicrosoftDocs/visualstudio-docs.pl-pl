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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b56996a5fa7cbf3c08842b783aa2d5dfc1131b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152887"
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
