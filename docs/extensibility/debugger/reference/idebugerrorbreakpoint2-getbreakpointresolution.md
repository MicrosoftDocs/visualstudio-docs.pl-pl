---
title: IDebugErrorBreakpoint2::GetBreakpointResolution | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpoint2::GetBreakpointResolution
helpviewer_keywords:
- IDebugErrorBreakpoint2::GetBreakpointResolution
ms.assetid: 1c2324ed-2a11-4e63-8f3a-f420c7a4018b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1b1ba346a24c22a01039736b53568a89684af92c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62874734"
---
# <a name="idebugerrorbreakpoint2getbreakpointresolution"></a>IDebugErrorBreakpoint2::GetBreakpointResolution
Pobiera rozwiązanie błąd punktu przerwania, który opisuje błąd.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetBreakpointResolution( 
   IDebugErrorBreakpointResolution2** ppErrorResolution
);
```

```csharp
int GetBreakpointResolution( 
   out IDebugErrorBreakpointResolution2 ppErrorResolution
);
```

#### <a name="parameters"></a>Parametry
 `ppErrorResolution`

 [out] Zwraca [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) obiektu, który opisuje błąd.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)