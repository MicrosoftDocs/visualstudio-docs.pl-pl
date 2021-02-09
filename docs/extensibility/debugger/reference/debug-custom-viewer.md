---
title: DEBUG_CUSTOM_VIEWER | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6fa8e8d9e07510a10b1b32534f3323dab4c84a22
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899108"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
Struktura, która identyfikuje niestandardowy Podgląd lub wizualizator typu.

## <a name="syntax"></a>Składnia

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>Elementy członkowskie
`dwID`\
Identyfikator umożliwiający odróżnienie wielu podglądów lub wizualizatorów implementowanych przez jeden `GUID` .

`bstrMenuName`\
Tekst, który będzie wyświetlany w menu rozwijanym.

`bstrDescription`\
Opis niestandardowej przeglądarki lub wizualizatora typu (musi być wartością null, jeśli nie jest używany).

`guidLang`\
Język przedstawiający ewaluatora wyrażeń.

`guidVendor`\
Dostawca przedstawiający ewaluatora wyrażeń.

`bstrMetric`\
Metryka, pod którą jest przechowywany niestandardowy Podgląd lub wizualizator typu `CLSID` .

## <a name="remarks"></a>Uwagi
Lista tej struktury jest zwracana przez wywołanie metody [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) (i według rozszerzenia, metody [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) ).

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
