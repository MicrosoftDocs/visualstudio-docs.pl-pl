---
title: IDebugExceptionEvent2::CanPassToDebuggee | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab57f599214cfbd7a1f5fcca15fa104b072d1d48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729869"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Określa, czy aparat debugowania (DE) obsługuje opcję przekazywania tego wyjątku do programu debugowanego po wznowieniu wykonywania.

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
 Zwraca albo `S_OK` (wyjątek może być przekazany `S_FALSE` do programu) lub (wyjątek nie może być przekazany).

## <a name="remarks"></a>Uwagi
 DE musi mieć domyślną akcję przekazywania do debuggee. IDE może odbierać [zdarzenie IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) i [wywołać Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) metody bez wywoływania `CanPassToDebuggee` metody. W związku z tym DE powinien mieć domyślny przypadek przekazywania wyjątku na lub nie.

## <a name="see-also"></a>Zobacz też
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Kontynuować](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
