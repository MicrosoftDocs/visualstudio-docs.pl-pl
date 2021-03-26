---
description: Ta metoda pobiera nowy obiekt wizualizatora.
title: 'IEEVisualizerDataProvider:: GetNewObjectForVisualizer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::GetNewObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::GetNewObjectForVisualizer method
ms.assetid: a898d549-4898-4fde-aad1-e8bb89129652
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af26455e37d0ecf881cd0bed898e1997f00a82ea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083352"
---
# <a name="ieevisualizerdataprovidergetnewobjectforvisualizer"></a>IEEVisualizerDataProvider::GetNewObjectForVisualizer
Ta metoda pobiera nowy obiekt wizualizatora. Ta metoda zawsze utworzy nowy obiekt z istniejącego obiektu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetNewObjectForVisualizer(
   IDebugObject** ppObject
);
```

```csharp
int GetNewObjectForVisualizer(
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametry
`ppObject`\
określoną Nowy obiekt.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 `This method` ponownie szacuje obiekt, który obecnie reprezentuje, i zwraca wynik jako nowy obiekt. Istniejący obiekt zostanie zaktualizowany w wyniku obliczania.

## <a name="see-also"></a>Zobacz też
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
