---
title: IPropertyProxyEESide::InitSourceDataProvider | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
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
[na zewnątrz] Zwraca obiekt [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda wykonuje wszystko, co jest niezbędne do zainicjowania obiektu, dzięki czemu można zwrócić interfejs [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) na dane obiektu. Dzięki temu dane obiektu mają być wyświetlane i, jeśli jest to dozwolone, zmieniane przez wizualizator typu.

## <a name="see-also"></a>Zobacz też
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
