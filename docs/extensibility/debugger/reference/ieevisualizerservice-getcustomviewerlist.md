---
title: IEEVisualizerService::GetCustomViewerList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b78afc3ace3764856fd0a83899be2eae597239e
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203672"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
Ta metoda zwraca listę wizualizatorów typu, które obsługującemu tej usługi.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetCustomViewerList(
   ULONG                celtSkip,
   ULONG                celtRequested,
   DEBUG_CUSTOM_VIEWER* rgViewers,
   ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
   uint                  celtSkip,
   uint                  celtRequested,
   DEBUG_CUSTOM_VIEWER[] rgViewers,
   out uint              pceltFetched
);
```

## <a name="parameters"></a>Parametry
`celtSkip`\
[in] Liczba wizualizatorów można pominąć.

`celRequested`\
[in] Liczba wizualizatorów do pobrania (również określa rozmiar `rgViewers` tablicy).

`rgViewers`\
[out w] Tablica [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) struktury do wypełnienia.

`pceltFetched`\
[out] Liczba wizualizatorów faktycznie pobrać.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) przekazuje żądanie do tej metody w ramach wsparcia dla wizualizatorów typu. Jeśli Ewaluator wyrażeń dostarcza również przeglądarek niestandardowych dla tego samego typu, można go dołączyć odpowiednio wypełniony [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) struktur dla tych przeglądarek niestandardowych do listy. Upewnij się, że [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) odzwierciedla te dodatkowe osoby przeglądające.

 Zobacz [Wizualizator typów i Przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Aby uzyskać szczegółowe informacje na temat różnic między wizualizatorów, a osoby przeglądające.

## <a name="see-also"></a>Zobacz także
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
- [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)