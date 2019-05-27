---
title: IDebugExceptionEvent2::GetException | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa6f4646894607823608b911c7a4e1df787fc05d
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66201140"
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