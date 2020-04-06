---
title: IPropertyProxyEESide::InPlaceUpdateObject | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79167b0f7e8094fabf80bb9b2d83c94ac874aa31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714890"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Aktualizuje dane obiektu o dany obiekt danych i zwraca nowy obiekt danych reprezentujący nowe dane obiektu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT InPlaceUpdateObject(
   [in] IEEDataStorage*   dataIn,
   [out] IEEDataStorage** dataOut
);
```

```csharp
int InPlaceUpdateObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parametry
`dataIn`\
[w] [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) obiekt zawierający nowe dane.

`dataOut`\
[na zewnątrz] Zwraca nowy `IEEDataStorage` obiekt zawierający zastąpione dane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda faktycznie aktualizuje dane obiektu. Dane w zwróconym [obiekcie IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nie muszą być takie `IEEDataStorage` same jak dane w obiekcie przychodzących, ale zwrócony obiekt musi odzwierciedlać bieżącą wartość właściwości.

 Obiekt danych przychodzących zazwyczaj nie jest implementowany przez EE. Jednak obiekt zwracany przez tę metodę jest zawsze implementowany przez EE, który umożliwia EE implementowania `IEEDataStorage` interfejsu na cokolwiek klasy jest pożądane.

 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) Metoda tworzy obiekt danych na podstawie obiektu danych przychodzących, ale nie wpływa na oryginalne dane właściwości.

## <a name="see-also"></a>Zobacz też
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
