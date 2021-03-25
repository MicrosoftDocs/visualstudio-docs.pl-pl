---
description: Ta metoda zwraca żądaną usługę.
title: 'IDebugBinder3:: GetEEService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ccc4d28a06d87d7c17d16470e10f259657083cc9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094305"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Ta metoda zwraca żądaną usługę.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetEEService(
   [in] GUID        vendor,
   [in] GUID        language,
   [in] GUID        iid,
   [out] IUnknown** ppService
);
```

```csharp
Int GetEEService(
   Guid       vendor,
   Guid       language,
   Guid       iid,
   out object ppService
);
```

## <a name="parameters"></a>Parametry
`vendor`\
[w] `GUID` dostawcy (wartość null jest akceptowalna).

`language`\
[w] `GUID` języka (wartość null jest akceptowalna).

`iid`\
[w] `IID` usługi do uzyskania.

`ppService`\
określoną Interfejs do żądanej usługi.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Przekaż `IID` Interfejs [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) ( `IID_IEEVisualizerServiceProvider` ), aby sprawdzić, czy usługa wizualizatora typów jest dostępna. Jeśli tak, ewaluatora wyrażeń może uzyskać Interfejs [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) do obsługi wizualizatorów typów. Zobacz [wizualizowanie i wyświetlanie danych,](../../../extensibility/debugger/visualizing-and-viewing-data.md) Aby uzyskać szczegółowe informacje.

## <a name="see-also"></a>Zobacz też
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [Wizualizacja i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md)
