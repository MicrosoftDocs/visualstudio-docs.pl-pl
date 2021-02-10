---
title: 'IDebugEngine2:: SetMetric | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4bb3c01b28f2d2c6e90616d389d9858d3346db72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933521"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Ta metoda ustawia wartość rejestru znaną jako Metryka.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
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
podczas Nazwa metryki.

`varValue`\
podczas Określa wartość metryki.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Metryka to wartość rejestru służąca do zmiany zachowania aparatu debugowania lub anonsowania obsługiwanych funkcji. Ta metoda umożliwia przekazanie wywołania do odpowiedniej formy [pomocników zestawu SDK na potrzeby funkcji debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` .

## <a name="see-also"></a>Zobacz też
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
