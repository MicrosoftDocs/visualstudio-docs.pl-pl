---
title: IPropertyProxyEESide::GetManagedViewerCreationData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 435f6924948ab1273abbded633bcce757b57d9b3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329512"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Pobiera informacje o viewer dla tego typu właściwości, aby utworzyć wystąpienia tego podglądu.

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
[out] Zwraca nazwę zestawu, zawierający ten obiekt.

`assemBytes`\
[out] Zwraca [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) obiekt zawierający ten obiekt (jest to wartość null Jeśli bajty nie są dostępne), w bajtach zestawu.

`assemPdb`\
[out] Zwraca `IEEDataStorage` obiekt, który zawiera symbol przechowywania informacji dla tego obiektu (jest to wartość null, jeśli nie symboli sklep jest dostępny).

`className`\
[out] Zwraca nazwę klasy zawierające ten obiekt.

`alr`\
[out] Zwraca wartość z zakresu od [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) Wyliczenie wskazujące lokalizacji zestawu.

`replacementOk`\
[out] Zwraca wartość różną od zera (`TRUE`) Jeśli wartość tego obiektu może zostać zmieniona; wartość zero (`FALSE`) Jeśli obiekt jest tylko do odczytu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest używana przez wizualizatorów typu tworzenia wystąpienia zarządzanego podglądu.

## <a name="see-also"></a>Zobacz także
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)