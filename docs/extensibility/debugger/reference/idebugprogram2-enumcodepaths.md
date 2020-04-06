---
title: IDebugProgram2::EnumCodePaths | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b99651811cedbdb8ec0eca5b766e6d75651dd5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723033"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Pobiera listę ścieżek kodu dla danej pozycji w pliku źródłowym.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumCodePaths( 
   LPCOLESTR            pszHint,
   IDebugCodeContext2*  pStart,
   IDebugStackFrame2*   pFrame,
   BOOL                 fSource,
   IEnumCodePaths2**    ppEnum,
   IDebugCodeContext2** ppSafety
);
```

```csharp
int EnumCodePaths( 
   string                 pszHint,
   IDebugCodeContext2     pStart,
   IDebugStackFrame2      pFrame,
   Int                    fSource,
   out IEnumCodePaths2    ppEnum,
   out IDebugCodeContext2 ppSafety
);
```

## <a name="parameters"></a>Parametry
`pszHint`\
[w] Wyraz pod kursorem w widoku **Źródło** lub **Demontaż** w IDE.

`pStart`\
[w] [Obiekt IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) reprezentujący bieżący kontekst kodu.

`pFrame`\
[w] Obiekt [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) reprezentujący ramkę stosu skojarzoną z bieżącym punktem przerwania.

`fSource`\
[w] Nonzero`TRUE`( ), jeśli w widoku`FALSE` **Źródłowym** lub zero ( ), jeśli w widoku **Demontaż.**

`ppEnum`\
[na zewnątrz] Zwraca obiekt [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) zawierający listę ścieżek kodu.

`ppSafety`\
[na zewnątrz] Zwraca obiekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) reprezentujący dodatkowy kontekst kodu, który ma zostać ustawiony jako punkt przerwania w przypadku pominięcia wybranej ścieżki kodu. Może się to zdarzyć na przykład w przypadku wyrażenia logicznego zwarcia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ścieżka kodu opisuje nazwę metody lub funkcji, która została wywołana, aby uzyskać do bieżącego punktu w wykonywaniu programu. Lista ścieżek kodu reprezentuje stos wywołań.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
