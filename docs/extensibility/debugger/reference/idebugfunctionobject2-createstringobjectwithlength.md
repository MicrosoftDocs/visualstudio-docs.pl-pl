---
title: IDebugFunctionObject2::CreateStringObjectWithLength | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ce0fdafc6835fdccc87638e17d3bbd01a1415abb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313506"
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
Tworzy obiekt ciągu, który ma określony czas.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CreateStringObjectWithLength (
   LPCOLESTR      pcstrString,
   UINT           uiLength,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObjectWithLength (
   string           pcstrString,
   uint             uiLength,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametry
`pcstrString`\
[in] Wartość ciągu z obiektem ciągu.

`uiLength`\
[in] Długość ciągu w bajtach.

`ppObject`\
[out] Zwraca [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiekt, który reprezentuje obiekt ciągu nowo utworzony.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)