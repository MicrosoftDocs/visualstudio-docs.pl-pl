---
description: Ustawia liczbę trafień dla powiązanego punktu przerwania.
title: 'IDebugBoundBreakpoint2:: SetHitCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetHitCount
helpviewer_keywords:
- SetHitCount method
- IDebugBoundBreakpoint2::SetHitCount method
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c7dbba43563a87a6c434d24014ce773375cd705c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167519"
---
# <a name="idebugboundbreakpoint2sethitcount"></a>IDebugBoundBreakpoint2::SetHitCount
Ustawia liczbę trafień dla powiązanego punktu przerwania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetHitCount( 
   DWORD dwHitCount
);
```

```csharp
int SetHitCount( 
   uint dwHitCount
);
```

## <a name="parameters"></a>Parametry
`dwHitCount`\
podczas Liczba trafień do ustawienia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwraca `E_BP_DELETED` czy stan powiązanego obiektu punktu przerwania jest ustawiony na `BPS_DELETED` (część wyliczenia [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) ).

## <a name="remarks"></a>Uwagi
 Licznik trafień wskazuje, ile razy ten punkt przerwania został wywołany podczas bieżącego przebiegu sesji.

 Ta metoda jest zwykle wywoływana przez aparat debugowania w celu zaktualizowania bieżącej liczby trafień w tym punkcie przerwania.

## <a name="see-also"></a>Zobacz też
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
