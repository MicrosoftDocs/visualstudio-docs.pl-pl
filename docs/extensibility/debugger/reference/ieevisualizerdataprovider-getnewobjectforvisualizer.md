---
title: IEEVisualizerDataProvider::GetNewObjectForVisualizer | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::GetNewObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::GetNewObjectForVisualizer method
ms.assetid: a898d549-4898-4fde-aad1-e8bb89129652
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bb1121786c07be83dac480474a5b3b934779beec
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66198868"
---
# <a name="ieevisualizerdataprovidergetnewobjectforvisualizer"></a>IEEVisualizerDataProvider::GetNewObjectForVisualizer
Ta metoda pobiera nowego obiektu dla wizualizatora. Ta metoda zawsze spowoduje utworzenie nowego obiektu z istniejących obiektów.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetNewObjectForVisualizer(
   IDebugObject** ppObject
);
```

```csharp
int GetNewObjectForVisualizer(
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametry
`ppObject`\
[out] Nowy obiekt.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 `This method` ponownie oblicza obiektu obecnie reprezentuje i zwraca wynik w postaci nowego obiektu. Istniejący obiekt zostanie zaktualizowany w wyniku oceny.

## <a name="see-also"></a>Zobacz także
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)