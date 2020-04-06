---
title: IDebugEngine2::CreatePendingBreakpoint | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f88cae3610487b92fed0d8390d44c55d3f536c4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731118"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Tworzy oczekujący punkt przerwania w silniku debugowania (DE).

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
[w] [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) obiekt, który opisuje oczekujących punkt przerwania do utworzenia.

`ppPendingBP`\
[na zewnątrz] Zwraca obiekt [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) reprezentujący oczekujący punkt przerwania.

## <a name="return-value"></a>Wartość zwracana
Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu. Zazwyczaj zwraca, `E_FAIL` `pBPRequest` jeśli parametr nie pasuje do żadnego języka `pBPRequest` obsługiwanego przez DE, jeśli parametr jest nieprawidłowy lub niekompletny.

## <a name="remarks"></a>Uwagi
Oczekujący punkt przerwania jest zasadniczo zbiór wszystkich informacji potrzebnych do powiązania punktu przerwania z kodem. Oczekujący punkt przerwania zwrócony z tej metody nie jest powiązany z kodem, dopóki nie zostanie wywołana metoda [Bind.](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

Dla każdego oczekującego punktu przerwania ustawia użytkownik, menedżer debugowania sesji (SDM) wywołuje tę metodę w każdym dołączonym DE. Do DE należy sprawdzenie, czy punkt przerwania jest prawidłowy dla programów uruchomionych w tym DE.

Gdy użytkownik ustawia punkt przerwania w wierszu kodu, DE jest wolny do powiązania punktu przerwania z najbliższym wierszu w dokumencie, który odpowiada temu kodowi. Dzięki temu użytkownik może ustawić punkt przerwania w pierwszym wierszu instrukcji wielowierszowej, ale powiązać go w ostatnim wierszu (gdzie cały kod jest przypisany w informacjach debugowania).

## <a name="example"></a>Przykład
W poniższym przykładzie pokazano, jak `CProgram` zaimplementować tę metodę dla prostego obiektu. De realizacji `IDebugEngine2::CreatePendingBreakpoint` może następnie przekazać wszystkie wywołania do tej implementacji metody w każdym programie.

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

## <a name="see-also"></a>Zobacz też
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
