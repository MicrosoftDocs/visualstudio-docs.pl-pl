---
description: Powiadamia aparat debugowania (DE), czy ma zostać zatrzymany w bieżącej lokalizacji kodu, czy po prostu kontynuuje wykonywanie.
title: 'IDebugCanStopEvent2:: Anuluj zatrzymanie | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38b4d528ae1aa5a89853dc4873a9c07aa051a14c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173639"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Powiadamia aparat debugowania (DE), czy ma zostać zatrzymany w bieżącej lokalizacji kodu, czy po prostu kontynuuje wykonywanie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CanStop ( 
   BOOL fCanStop
);
```

```csharp
int CanStop ( 
   int fCanStop
);
```

## <a name="parameters"></a>Parametry
`fCanStop`\
podczas Wartość niezerowa ( `TRUE` ), jeśli de powinna zatrzymać się w bieżącej lokalizacji kodu; w przeciwnym razie, zero ( `FALSE` ).

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Odbiorca tego zdarzenia zazwyczaj wywołuje metodę [getpowód](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) , aby ustalić przyczynę zatrzymania, a następnie wywołuje `IDebugCanStopEvent2::CanStop` metodę z odpowiednią odpowiedzią.

 Jeśli ANULUJe, wysyła Zdarzenie opisujące powód zatrzymywania. Zazwyczaj są wysyłane dwa zdarzenia, czyli przerwanie użytkownika lub sygnału reprezentowane przez interfejs [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) oraz zdarzenie punktu przerwania reprezentowane przez interfejs [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
