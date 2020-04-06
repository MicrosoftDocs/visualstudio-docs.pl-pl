---
title: IDebugThread2::EnumFrameInfo | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bd3c6d46a577930cc7a2b87c85cd82a55f8cf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718860"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Pobiera listę ramek stosu dla tego wątku.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumFrameInfo ( 
   FRAMEINFO_FLAGS        dwFieldSpec,
   UINT                   nRadix,
   IEnumDebugFrameInfo2** ppEnum
);
```

```csharp
int EnumFrameInfo ( 
   enum_FRAMEINFO_FLAGS     dwFieldSpec,
   uint                     nRadix,
   out IEnumDebugFrameInfo2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`dwFieldSpec`\
[w] Kombinacja flag z wyliczenia [FRAMEINFO_FLAGS,](../../../extensibility/debugger/reference/frameinfo-flags.md) która określa, które pola struktur [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) mają być wypełnione. Określ `FIF_FUNCNAME_FORMAT` flagę, aby sformatować nazwę funkcji w jeden ciąg.

`nRadix`\
[w] Radix używany do formatowania informacji liczbowych w wyliczaczy.

`ppEnum`\
[na zewnątrz] Zwraca obiekt [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) zawierający listę struktur [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) opisujących ramkę stosu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ramki wątku są wyliczone w kolejności, z bieżącą ramką wyliczoną jako pierwsza i najstarszą ramką wyliczoną jako ostatnia.

## <a name="see-also"></a>Zobacz też
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
