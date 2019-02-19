---
title: IDebugCodeContext3::GetProcess | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugCodeContext3::GetProcess
ms.assetid: e082e494-2255-4d9d-a5a9-6dadd904bea8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f892e9ee339f25f512c4036fb9e794c922b7404
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413179"
---
# <a name="idebugcodecontext3getprocess"></a>IDebugCodeContext3::GetProcess
Pobiera odwołanie do interfejsu debugowania procesu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetProcess(
    IDebugProcess2 **ppProcess
);
```

```csharp
public int GetProcess(
    out IDebugProcess2 ppProcess
);
```

#### <a name="parameters"></a>Parametry
`ppProcess`  
[out] Odwołanie do interfejsu debugowania procesu.

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę, aby uzyskać **CDebugCodeContext** obiekt ujawniający [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) interfejsu.

```cpp
HRESULT CDebugCodeContext::GetProcess(IDebugProcess2** ppProcess)
{
    HRESULT hr = S_OK;
    CComPtr<CDebugEngine> pEngine;
    CComPtr<IDebugPort2> pPort2;

    IfFalseGo( ppProcess, E_INVALIDARG );
    *ppProcess = NULL;

    IfFalseGo( m_pProgram, E_FAIL );
    IfFailGo( ((CDebugProgram *)m_pProgram)->GetEngine(&pEngine) );
    IfFailGo( pEngine->GetSDMProcess(ppProcess) );

Error:

    return hr;
}
```

## <a name="see-also"></a>Zobacz też
[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)
