---
description: Pobiera strumień demontażu dla tego programu lub części tego programu.
title: 'IDebugProgram2:: GetDisassemblyStream | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c7016c003642b9ef2688390de7cdb39be412bded
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075903"
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
podczas Określa wartość z wyliczenia [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) , która definiuje zakres strumienia demontażu.

`pCodeContext`\
podczas Obiekt [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , który reprezentuje położenie lokalizacji, w której ma zostać rozpoczęty strumień.

`ppDisassemblyStream`\
określoną Zwraca obiekt [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) , który reprezentuje strumień deasemblera.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwraca `E_DISASM_NOTSUPPORTED` Jeśli demontaż nie jest obsługiwany dla tej konkretnej architektury.

## <a name="remarks"></a>Uwagi
 Jeśli `dwScopes` parametr ma `DSS_HUGE` flagę zestawu [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) , wówczas demontaż powinien zwrócić dużą liczbę instrukcji odnoszących się do zestawu, na przykład dla całego pliku lub modułu. Jeśli `DSS_HUGE` flaga nie jest ustawiona, demontaż powinien być ograniczony do małego regionu, zazwyczaj w przypadku pojedynczej funkcji.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
