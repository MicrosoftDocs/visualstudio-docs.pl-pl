---
title: IEEVisualizerDataProvider::CanSetObjectForVisualizer | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::CanSetObjectForVisualizer method
ms.assetid: 70fd3c6f-2f82-43a3-993b-c1dc8aa080bf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71fe6ed16bd1e80a13cfe97fe5ebcf84bc140da4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335611"
---
# <a name="ieevisualizerdataprovidercansetobjectforvisualizer"></a>IEEVisualizerDataProvider::CanSetObjectForVisualizer
Ta metoda określa, czy wizualizatora może mieć obiektu danych, który reprezentuje zaktualizowany.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CanSetObjectForVisualizer(
   BOOL* b
);
```

```csharp
int CanSetObjectForVisualizer(
   out int b
);
```

## <a name="parameters"></a>Parametry
`b`\
[out] Wartość różną od zera (`TRUE`) można zaktualizować obiektu w wizualizatora, wartość zero (`FALSE`) Jeśli jest ona nieosiągalna.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Obiekt nie może być zmieniane, jeśli jest powiązany z pamięci tylko do odczytu, na przykład.

## <a name="see-also"></a>Zobacz także
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)