---
title: IPropertyProxyEESide::GetManagedViewerCreationData | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e72922b348c8744f10037e199e93f735ff4be8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714963"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Pobiera informacje o przeglądarce dla tego typu właściwości w celu wystąpienia tej przeglądarki.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetManagedViewerCreationData(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  className,
   ASSEMBLYLOCRESOLUTION* alr,
   BOOL*                  replacementOk
);
```

```csharp
int GetManagedViewerCreationData(
   out string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     className,
   out enum_ASSEMBLYLOCRESOLUTION alr,
   out int                        replacementOk
);
```

## <a name="parameters"></a>Parametry
`assemName`\
[na zewnątrz] Zwraca nazwę zestawu, w którym ten obiekt.

`assemBytes`\
[na zewnątrz] Zwraca obiekt [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) zawierający bajty zestawu tego obiektu (jest to wartość null, jeśli nie są dostępne bajty).

`assemPdb`\
[na zewnątrz] Zwraca `IEEDataStorage` obiekt zawierający informacje magazynu symboli dla tego obiektu (jest to wartość null, jeśli nie jest dostępny żaden magazyn symboli).

`className`\
[na zewnątrz] Zwraca nazwę klasy zawierającą ten obiekt.

`alr`\
[na zewnątrz] Zwraca wartość z wyliczenia [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) wskazującego położenie złożenia.

`replacementOk`\
[na zewnątrz] Zwraca wartość niezerową (`TRUE`), jeśli można zmienić wartość tego obiektu; zero`FALSE`( ), jeśli obiekt jest tylko do odczytu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest używana przez wizualizatorów typu do tworzenia wystąpienia zarządzanej przeglądarki.

## <a name="see-also"></a>Zobacz też
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
