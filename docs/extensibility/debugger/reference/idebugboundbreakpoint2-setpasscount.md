---
title: IDebugBoundBreakpoint2::SetPassCount | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bcc7bd57ce0c392a2874f107c6e4d8d5753399d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735432"
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
Ustawia lub zmienia liczbę przebiegów skojarzonych z tym powiązanym punktem przerwania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>Parametry
`bpPassCount`\
[w] Struktura [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) określająca liczbę przebiegów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu. Zwraca `E_BP_DELETED` wartość, jeśli stan obiektu powiązanego `BPS_DELETED` punktu przerwania jest ustawiony na (część wyliczenia [BP_STATE).](../../../extensibility/debugger/reference/bp-state.md)

## <a name="remarks"></a>Uwagi
 Liczba przebiegów określa, kiedy punkt przerwania jest uruchamiany. Bieżący przebieg lub liczba trafień można uzyskać, wywołując [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) metody.

 Każda liczba przebiegów, która była wcześniej skojarzona z tym punktem przerwania, jest tracona.

## <a name="see-also"></a>Zobacz też
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
