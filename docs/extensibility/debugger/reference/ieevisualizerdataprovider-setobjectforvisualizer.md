---
title: IEEVisualizerDataProvider::SetObjectForVisualizer | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a55328c4148aa911d86b8f2daf05ba84a50ff444
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62867979"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Ta metoda zmienia obiekt, który reprezentuje wizualizatora.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetObjectForVisualizer(
   IDebugObject*  pNewObject,
   BSTR*          error,
   IDebugObject** pException
);
```

```csharp
int SetObjectForVisualizer(
   IDebugObject     pNewObject,
   out string       error,
   out IDebugObject pException
);
```

#### <a name="parameters"></a>Parametry
 `pNewObject`

 [in] Obiekt, który można ustawić.

 `error`

 [out] Jeśli wystąpił błąd podczas ustawiania obiektu, ten ciąg zawiera komunikat o błędzie.

 `pException`

 [out] Jeśli wystąpił błąd, ten obiekt przechowuje informacje o wyjątku.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jest implementujący, aby określić, jak informacje o błędzie jest zwracana. Jednak jest możliwe, że niektóre obiekty wywołujące mogą tylko wygląd, aby zobaczyć, jeśli obiekt wyjątku został zwrócony wiedzieć, był błąd, więc ta metoda zawsze powinna zwracać obiekt wyjątku, jeśli wystąpił błąd. W przypadku, gdy obiekt wywołujący chce mieć należy również dostarczyć ciąg błędu z niego korzystać.

## <a name="see-also"></a>Zobacz też
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)