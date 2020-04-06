---
title: IDebugExceptionEvent2::PassToDebuggee | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aec6f460295b59b2b5455b83d5b0be554bca24fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729833"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Określa, czy wyjątek powinien być przekazywany do programu debugowanego po wznowieniu wykonywania lub jeśli wyjątek powinien zostać odrzucony.

## <a name="syntax"></a>Składnia

```cpp
HRESULT PassToDebuggee(
   BOOL fPass
);
```

```csharp
int PassToDebuggee(
   int fPass
);
```

## <a name="parameters"></a>Parametry
`fPass`\
[w] Nonzero`TRUE`( ), jeśli wyjątek powinien być przekazany do programu debugowanego po`FALSE`wznowieniu wykonywania lub zero ( ), jeśli wyjątek powinien zostać odrzucony.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wywołanie tej metody faktycznie nie powoduje, że kod ma być wykonywany w debugowanym programie. Wywołanie jest po prostu ustawić stan dla następnego wykonania kodu. Na przykład wywołania [canpasstodebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) metoda `S_OK` może powrócić z [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` pole ustawione `EXCEPTION_STOP_SECOND_CHANCE`na .

 IDE może odbierać [zdarzenie IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) i [wywołać Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md) metody. Aparat debugowania (DE) powinien mieć domyślne zachowanie `PassToDebuggee` do obsługi sprawy, jeśli metoda nie jest wywoływana.

## <a name="see-also"></a>Zobacz też
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Kontynuować](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
