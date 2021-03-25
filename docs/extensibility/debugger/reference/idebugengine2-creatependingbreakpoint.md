---
description: Tworzy oczekujący punkt przerwania w aparacie debugowania (DE).
title: 'IDebugEngine2:: CreatePendingBreakpoint | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa06a4c88afecfebbd0b1258d7f1830dfdaad5ac
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093876"
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
podczas Obiekt [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) , który opisuje oczekujący punkt przerwania do utworzenia.

`ppPendingBP`\
określoną Zwraca obiekt [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) , który reprezentuje oczekujący punkt przerwania.

## <a name="return-value"></a>Wartość zwracana
Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwykle zwraca `E_FAIL` , jeśli `pBPRequest` parametr nie jest zgodny z żadnym językiem obsługiwanym przez de z, jeśli `pBPRequest` parametr jest nieprawidłowy lub niekompletny.

## <a name="remarks"></a>Uwagi
Oczekujący punkt przerwania jest zasadniczo kolekcją wszystkich informacji niezbędnych do powiązania punktu przerwania z kodem. Oczekujący punkt przerwania zwrócony przez tę metodę nie jest powiązany z kodem do momentu wywołania metody [bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) .

Dla każdego oczekującego punktu przerwania ustawionego przez użytkownika Menedżer debugowania sesji (SDM) wywołuje tę metodę w każdej dołączonej. Należy sprawdzić, czy punkt przerwania jest prawidłowy dla programów uruchomionych w tym elemencie.

Gdy użytkownik ustawia punkt przerwania w wierszu kodu, to DE jest bezpłatny, aby powiązać punkt przerwania z najbliższym wierszem w dokumencie, który odnosi się do tego kodu. Dzięki temu użytkownik może ustawić punkt przerwania w pierwszym wierszu instrukcji wielowierszowej, ale powiązać ją z ostatnim wierszem (gdzie cały kod jest przypisany do informacji debugowania).

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę dla prostego `CProgram` obiektu. Po COFNIĘCIu implementacji `IDebugEngine2::CreatePendingBreakpoint` można przesłać dalej wszystkie wywołania tej implementacji metody w każdym programie.

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
- [Węglowodor](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
