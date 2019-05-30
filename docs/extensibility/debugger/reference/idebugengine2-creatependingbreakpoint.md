---
title: IDebugEngine2::CreatePendingBreakpoint | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fdd7fde0540754df3b152eb38d729576a7b9fe26
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333304"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Tworzy oczekujący punkt przerwania w aparacie debugowania (DE).

## <a name="syntax"></a>Składnia

```cpp
HRESULT CreatePendingBreakpoint(
    IDebugBreakpointRequest2*  pBPRequest,
    IDebugPendingBreakpoint2** ppPendingBP
);
```

```csharp
int CreatePendingBreakpoint(
    IDebugBreakpointRequest2     pBPRequest,
    out IDebugPendingBreakpoint2 ppPendingBP
);
```

## <a name="parameters"></a>Parametry
`pBPRequest`\
[in] [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) obiekt, który opisuje oczekujący punkt przerwania, aby utworzyć.

`ppPendingBP`\
[out] Zwraca [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) obiekt, który reprezentuje oczekujący punkt przerwania.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwykle zwraca `E_FAIL` Jeśli `pBPRequest` parametru jest niezgodny z dowolnego języka, obsługiwane przez DE, jeśli `pBPRequest` parametru jest nieprawidłowa lub niekompletna.

## <a name="remarks"></a>Uwagi
Oczekujący punkt przerwania jest zasadniczo zbiorem wszystkie informacje potrzebne, aby powiązać punkt przerwania z kodu. Oczekujący punkt przerwania, zwrócone w wyniku tej metody nie jest powiązany z kodu do czasu [powiązać](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) metoda jest wywoływana.

Dla wszystkich oczekujących punktów przerwania zestawów użytkownika, Menedżer debugowania sesji (SDM) wywołuje tę metodę w każdym DE dołączone. Jest DE, aby sprawdzić, czy punkt przerwania jest prawidłowa dla programów uruchomionych w tym DE.

Gdy użytkownik ustawia punkt przerwania w wierszu kodu, DE jest bezpłatne powiązać punkt przerwania do najbliższego wiersza w dokumencie, który odnosi się do tego kodu. Dzięki temu użytkownik może ustawić punkt przerwania w pierwszym wierszu instrukcję wiele wierszy, ale powiązać go z ostatniego wiersza (w którym przypisać cały kod w informacjach debugowania).

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę dla prostego `CProgram` obiektu. Implementacja DE `IDebugEngine2::CreatePendingBreakpoint` można następnie przesyła wszystkie wywołania do tej implementacji metody w każdym programie.

```
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)
{
    // Create and initialize the CPendingBreakpoint object.
    CComObject<CPendingBreakpoint> *pPending;
    CComObject<CPendingBreakpoint>::CreateInstance(&pPending);
    pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);
    return pPending->QueryInterface(ppPendingBP);
}
```

## <a name="see-also"></a>Zobacz także
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
