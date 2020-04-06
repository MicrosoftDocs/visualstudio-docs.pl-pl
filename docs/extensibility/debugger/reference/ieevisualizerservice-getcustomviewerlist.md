---
title: IEEVisualizerService::GetCustomViewerList | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f3808ad6fb511270ee3825601c476f10a8b77124
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718017"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
Ta metoda zwraca listę wizualizatorów typu, o których ta usługa wie.

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
[w] Liczba wizualizatorów do przeskoczyć.

`celRequested`\
[w] Liczba wizualizatorów do pobrania (określa `rgViewers` również rozmiar tablicy).

`rgViewers`\
[w, na zewnątrz] Tablica [struktur DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) do wypełnienia.

`pceltFetched`\
[na zewnątrz] Liczba wizualizatorów faktycznie pobranych.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) przekazuje żądanie do tej metody w ramach obsługi wizualizatorów typu. Jeśli oceniający wyrażenie dostarcza również niestandardowe przeglądarki dla tego samego typu, może dołączyć odpowiednio wypełnione [struktury DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) dla tych niestandardowych widzów do listy. Upewnij się, że [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) odzwierciedla te dodatkowe przeglądarki.

 Zobacz [Wizualizator typów i Podgląd niestandardowy, aby](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) uzyskać szczegółowe informacje na temat różnic między wizualizatorami a przeglądarkami.

## <a name="see-also"></a>Zobacz też
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
- [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
