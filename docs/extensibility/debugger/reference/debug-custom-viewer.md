---
title: DEBUG_CUSTOM_VIEWER | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f50f46376e21694bebeb4f13ab8ed8e658838bf2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680459"
---
# <a name="debugcustomviewer"></a>DEBUG_CUSTOM_VIEWER
Struktura, która identyfikuje podglądu niestandardowego lub typu wizualizatora.

## <a name="syntax"></a>Składnia

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>Elementy członkowskie
dwID identyfikator do rozróżnienia wielu osób przeglądających lub wizualizatorów implementowane za pomocą jednej `GUID`.

bstrMenuName tekst, który będzie wyświetlany w menu rozwijanym.

Opis bstrDescription A Przeglądarka niestandardowa lub Wizualizator typów (musi być wartością null Jeśli nie są używane).

guidLang języka dostarczanie Ewaluator wyrażeń.

guidVendor dostawcy dostarczanie Ewaluator wyrażeń.

bstrMetric metryki w ramach której przeglądarka niestandardowa lub typu wizualizatora `CLSID` są przechowywane.

## <a name="remarks"></a>Uwagi
Lista ta struktura jest zwracany przez wywołanie [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) — metoda (a w konsekwencji, [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) metody).

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
