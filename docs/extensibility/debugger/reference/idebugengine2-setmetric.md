---
title: IDebugEngine2::SetMetric | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: caada8db1791d94e7a9632394cd4659bf8cec3a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730894"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Ta metoda ustawia wartość rejestru znaną jako metryka.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
);
```

```csharp
int SetMetric(
   string pszMetric,
   object varValue
);
```

## <a name="parameters"></a>Parametry
`pszMetric`\
[w] Nazwa metryki.

`varValue`\
[w] Określa wartość metryki.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Metryka jest wartością rejestru używaną do zmiany zachowania aparatu debugowania lub do anonsowania obsługiwanych funkcji. Ta metoda może przesłać wywołanie do odpowiedniej formy [pomocnika SDK dla funkcji debugowania,](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric`.

## <a name="see-also"></a>Zobacz też
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
