---
title: 'IPropertyProxyEESide:: InPlaceUpdateObject | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714890"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Aktualizuje dane obiektu za pomocą podanego obiektu danych i zwraca nowy obiekt danych reprezentujący nowe dane obiektu.

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
podczas Obiekt [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) zawierający nowe dane.

`dataOut`\
określoną Zwraca nowy `IEEDataStorage` obiekt zawierający zastąpione dane.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda faktycznie aktualizuje dane obiektu. Dane w zwracanym obiekcie [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) nie muszą być takie same jak dane w obiekcie przychodzącym `IEEDataStorage` , ale zwracany obiekt musi odzwierciedlać bieżącą wartość właściwości.

 Obiekt danych przychodzących zazwyczaj nie jest implementowany przez EE. Jednak obiekt zwrócony przez tę metodę jest zawsze zaimplementowany przez EE, co umożliwia implementację `IEEDataStorage` interfejsu na dowolnej klasie.

 Metoda [zastępująca](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) tworzy obiekt danych na podstawie przychodzącego obiektu danych, ale nie wpływa na oryginalne dane właściwości.

## <a name="see-also"></a>Zobacz też
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
