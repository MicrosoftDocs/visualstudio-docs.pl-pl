---
title: IDebugStackFrame2::GetInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetInfo
helpviewer_keywords:
- IDebugStackFrame2::GetInfo
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71bb25e93cc1a3f97e61e269270cd87a0bc36558
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209969"
---
# <a name="idebugstackframe2getinfo"></a>IDebugStackFrame2::GetInfo
Pobiera opis ramki stosu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetInfo ( 
   FRAMEINFO_FLAGS dwFieldSpec,
   UINT            nRadix,
   FRAMEINFO*      pFrameInfo
);
```

```csharp
int GetInfo ( 
   enum_FRAMEINFO_FLAGS dwFieldSpec,
   uint                 nRadix,
   FRAMEINFO[]          pFrameInfo
);
```

## <a name="parameters"></a>Parametry
`dwFieldSpec`\
[in] Kombinacja flag z [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) wyliczenie, które określa, które pola `pFrameInfo` parametru są wypełniane.

`nRadix`\
[in] Podstawy, który ma być używany w formatowaniu wszelkie dane liczbowe.

`pFrameInfo`\
[out] A [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strukturę, która jest wypełniane opis ramki stosu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)