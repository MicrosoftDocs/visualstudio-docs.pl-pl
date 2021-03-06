---
description: Ta metoda zmienia obiekt, który reprezentuje wizualizator.
title: 'IEEVisualizerDataProvider:: SetObjectForVisualizer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df5cfd2acef1a2214d4692a49c742c26cd420ffa
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227232"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Ta metoda zmienia obiekt, który reprezentuje wizualizator.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetObjectForVisualizer(
   IDebugObject*  pNewObject,
   BSTR*          error,
   IDebugObject** pException
);
```

```csharp
int SetObjectForVisualizer(
   IDebugObject     pNewObject,
   out string       error,
   out IDebugObject pException
);
```

## <a name="parameters"></a>Parametry
`pNewObject`\
podczas Obiekt, który ma zostać ustawiony.

`error`\
określoną Jeśli wystąpił błąd podczas ustawiania obiektu, ten ciąg zawiera komunikat o błędzie.

`pException`\
określoną Jeśli wystąpił błąd, ten obiekt zawiera informacje o wyjątku.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Aby określić, jak są zwracane informacje o błędzie, należy do realizatorów. Jednak istnieje możliwość, że niektóre obiekty wywołujące mogą jedynie zobaczyć, czy obiekt wyjątku został zwrócony, aby wiedzieć, że wystąpił błąd, dlatego ta metoda powinna zawsze zwracać obiekt wyjątku, jeśli wystąpił błąd. Ciąg błędu należy również podać w przypadku, gdy obiekt wywołujący chce, aby go użyć.

## <a name="see-also"></a>Zobacz też
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
