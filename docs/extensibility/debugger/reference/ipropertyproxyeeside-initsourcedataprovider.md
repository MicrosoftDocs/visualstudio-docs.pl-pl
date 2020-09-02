---
title: 'IPropertyProxyEESide:: InitSourceDataProvider | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f14f24836beb1d69a15149a56a2817ebf14eff55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714909"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
Inicjuje dane źródłowe dla tego obiektu i zwraca obiekt zawierający dane początkowe.

## <a name="syntax"></a>Składnia

```cpp
HRESULT InitSourceDataProvider(
   IEEDataStorage** dataOut
);
```

```csharp
int InitSourceDataProvider(
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parametry
`dataOut`\
określoną Zwraca obiekt [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wymagana do zainicjowania obiektu, aby mógł zwrócić Interfejs [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) na dane obiektu. Pozwala to na wyświetlanie danych obiektu i, jeśli jest to dozwolone, przez wizualizatora typu.

## <a name="see-also"></a>Zobacz też
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
