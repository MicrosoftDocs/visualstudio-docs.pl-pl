---
title: IDebugExceptionEvent2::GetException | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::GetException
helpviewer_keywords:
- IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 332cbb28bd175aa5c3b4187ae735a479ba9de6b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729859"
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Pobiera szczegółowy opis wyjątku, który został zgłoszony to zdarzenie.

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
[w, na zewnątrz] [Struktura EXCEPTION_INFO,](../../../extensibility/debugger/reference/exception-info.md) która jest wypełniona opisem wyjątku.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi

 [Tylko C++] Obiekt wywołujący jest odpowiedzialny za zwalnianie ciągów w [strukturze EXCEPTION_INFO,](../../../extensibility/debugger/reference/exception-info.md) a także zwalnianie obiektu [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) w strukturze.

## <a name="see-also"></a>Zobacz też
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
