---
title: IDebugProgram2::EnumCodePaths | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodePaths
helpviewer_keywords:
- IDebugProgram2::EnumCodePaths
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3206a9c89197ccc9415115fe9fb0995e51ede8c9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353188"
---
# <a name="idebugprogram2enumcodepaths"></a>IDebugProgram2::EnumCodePaths
Pobiera listę ścieżek kodu dla danego stanowiska w pliku źródłowym.

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
[in] Word pod kursorem w **źródła** lub **dezasemblacji** widoku w środowisku IDE.

`pStart`\
[in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiekt reprezentujący bieżący kontekst kodu.

`pFrame`\
[in] [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) obiekt reprezentujący ramkę stosu skojarzone z bieżącym punktu przerwania.

`fSource`\
[in] Wartość różną od zera (`TRUE`) Jeśli w **źródła** widoku lub zero (`FALSE`) Jeśli w **dezasemblacji** widoku.

`ppEnum`\
[out] Zwraca [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) obiekt, który zawiera listę ścieżek kodu.

`ppSafety`\
[out] Zwraca [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiektów reprezentującą kontekst dodatkowy kod ma być ustawiona jako punkt przerwania, w przypadku, gdy wybrana kodu ścieżka zostanie pominięta. Może to nastąpić w przypadku zwartym wyrażenie logiczne, np.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ścieżka kodu w tym artykule opisano nazwę metody lub funkcji, która została wywołana, aby uzyskać dostęp do bieżącego punktu podczas wykonywania programu. Lista ścieżek kodu przedstawia stos wywołań.

## <a name="see-also"></a>Zobacz także
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)