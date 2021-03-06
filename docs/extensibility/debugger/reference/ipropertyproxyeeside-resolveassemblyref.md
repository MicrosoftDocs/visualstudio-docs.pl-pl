---
description: Określa lokalizację określonego odwołania do zestawu zarządzanego.
title: 'IPropertyProxyEESide:: ResolveAssemblyRef | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 687ca5922cc59322c37b7b391a9b5f40d52c14ad
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225581"
---
# <a name="ipropertyproxyeesideresolveassemblyref"></a>IPropertyProxyEESide::ResolveAssemblyRef
Określa lokalizację określonego odwołania do zestawu zarządzanego.

## <a name="syntax"></a>Składnia

```cpp
HRESULT ResolveAssemblyRef(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  assemLocation,
   ASSEMBLYLOCRESOLUTION* alr
);
```

```csharp
int ResolveAssemblyRef(
   ref string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     assemLocation,
   out enum_ASSEMBLYLOCRESOLUTION alr
);
```

## <a name="parameters"></a>Parametry
`assemName`\
podczas Nazwa zestawu do rozwiązania.

`assemBytes`\
określoną Zwraca obiekt [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) zawierający bajty zestawu skojarzone z odwołaniem.

`assemPdb`\
określoną Zwraca `IEEDataStorage` obiekt zawierający dane magazynu symboli skojarzone z tym odwołaniem.

`assemLocation`\
określoną Zwraca lokalizację ścieżki tego odwołania.

`alr`\
określoną Zwraca wartość z wyliczenia [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) wskazujący lokalizację zestawu odwołania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda nie jest zwykle implementowana przez niestandardową ewaluatora wyrażeń.

## <a name="see-also"></a>Zobacz też
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
