---
title: IDebugProgram2::GetDisassemblyStream | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71389ef210d50becaab4d25e29194c2a40000497
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66308765"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Pobiera strumień dezasemblacji dla tego programu lub jej część tego programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetDisassemblyStream( 
   DISASSEMBLY_STREAM_SCOPE   dwScope,
   IDebugCodeContext2*        pCodeContext,
   IDebugDisassemblyStream2** ppDisassemblyStream
);
```

```csharp
int GetDisassemblyStream( 
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,
   IDebugCodeContext2             pCodeContext,
   out IDebugDisassemblyStream2   ppDisassemblyStream
);
```

## <a name="parameters"></a>Parametry
`dwScope`\
[in] Określa wartość z zakresu od [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) wyliczenia, która określa zakres strumienia dezasemblacji.

`pCodeContext`\
[in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiekt, który reprezentuje pozycję gdzie zacząć strumienia dezasemblacji.

`ppDisassemblyStream`\
[out] Zwraca [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) obiekt, który reprezentuje strumień dezasemblacji.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `E_DISASM_NOTSUPPORTED` Jeśli dezasemblacji nie jest obsługiwana dla tej konkretnej architektury.

## <a name="remarks"></a>Uwagi
 Jeśli `dwScopes` parametr ma `DSS_HUGE` flagę [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) Ustaw wyliczenia, a następnie demontaż powinien zwrócić dużą liczbę instrukcji dezasemblacji, na przykład dla całego pliku lub modułu. Jeśli `DSS_HUGE` nie jest ustawiona flaga, a następnie demontaż powinien być ograniczone do regionu małe, zazwyczaj z pojedynczą funkcję.

## <a name="see-also"></a>Zobacz także
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)