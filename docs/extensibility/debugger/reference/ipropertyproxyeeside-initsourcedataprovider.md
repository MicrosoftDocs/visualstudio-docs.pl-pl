---
title: IPropertyProxyEESide::InitSourceDataProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fb0d2b960c2bafd1a2d502e41c8a435a5205d11
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687487"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
Inicjuje źródło danych pod kątem tego obiektu i zwraca obiekt zawierający dane pierwotne.

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

#### <a name="parameters"></a>Parametry
 `dataOut`

 [out] Zwraca [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) obiektu

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda wykonuje, niezależnie od rodzaju jest niezbędne do zainicjowania obiektu, dzięki czemu może zwracać [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) interfejsu na obiekt danych. Dzięki temu danych obiektu do wyświetlania i, jeśli jest to dozwolone, zmienione przez Wizualizator typów.

## <a name="see-also"></a>Zobacz też
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)