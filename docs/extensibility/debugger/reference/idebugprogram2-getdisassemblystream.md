---
title: IDebugProgram2::GetDisassemblyStream | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2160f963ad1f3f37291519ced30b8096e33a6116
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722864"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Pobiera strumień demontażu dla tego programu lub części tego programu.

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
[w] Określa wartość z [wyliczenia DISASSEMBLY_STREAM_SCOPE,](../../../extensibility/debugger/reference/disassembly-stream-scope.md) która definiuje zakres strumienia demontażu.

`pCodeContext`\
[w] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) obiekt, który reprezentuje położenie, gdzie można uruchomić strumień demontażu.

`ppDisassemblyStream`\
[na zewnątrz] Zwraca [obiekt IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) reprezentujący strumień demontażu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu. Zwraca, `E_DISASM_NOTSUPPORTED` jeśli demontaż nie jest obsługiwany dla tej konkretnej architektury.

## <a name="remarks"></a>Uwagi
 Jeśli `dwScopes` parametr ma `DSS_HUGE` flagę [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) zestaw wyliczenia, a następnie demontażu oczekuje się zwrócić dużą liczbę instrukcji demontażu, na przykład dla całego pliku lub modułu. Jeśli `DSS_HUGE` flaga nie jest ustawiona, a następnie demontażu oczekuje się, że ogranicza się do małego regionu, zazwyczaj jednej funkcji.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
