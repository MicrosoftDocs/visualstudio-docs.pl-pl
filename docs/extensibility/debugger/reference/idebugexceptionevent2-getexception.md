---
title: IDebugExceptionEvent2::GetException | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 691df8f5a212f1d854d87076a215402c7ce0053c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310505"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Pobiera szczegółowy opis wyjątku, która wywołała zdarzenie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetException( 
   EXCEPTION_INFO* pExceptionInfo
);
```

```csharp
int GetException( 
   EXCEPTION_INFO[] pExceptionInfo
);
```

## <a name="parameters"></a>Parametry
`pExceptionInfo`\
[out w] [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) strukturę, która jest wypełniane opis wyjątku.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi

 [C++ tylko] Obiekt wywołujący jest odpowiedzialny za zwalnianie wszystkie ciągi w [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struktury, a także udostępnia [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiektu w strukturze.

## <a name="see-also"></a>Zobacz także
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)