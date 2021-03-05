---
description: Pobiera opis ramki stosu.
title: 'IDebugStackFrame2:: GetInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetInfo
helpviewer_keywords:
- IDebugStackFrame2::GetInfo
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3af7aafe43c0d7916a3fc11b855d5512f50a1d5f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168624"
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
podczas Kombinacja flag z wyliczenia [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) , która określa, które pola `pFrameInfo` parametru mają być wypełnione.

`nRadix`\
podczas Podstawy do użycia podczas formatowania wszelkich informacji numerycznych.

`pFrameInfo`\
określoną Struktura [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) , która jest wypełniana opisem ramki stosu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
