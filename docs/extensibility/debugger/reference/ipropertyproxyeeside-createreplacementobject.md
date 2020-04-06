---
title: IPropertyProxyEESide::CreateReplacementObject | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f449a505c56c180f1bab021007f1b635a2461996
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715037"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Tworzy kopię obiektu danych specyficznego dla oceniającego wyrażenie (EE).

## <a name="syntax"></a>Składnia

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parametry
`dataIn`\
[w] [Obiekt IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) przechowujący dane do skopiowania.

`dataOut`\
[na zewnątrz] Zwraca nowy `IEEDataStorage` obiekt.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest podana [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) obiektu reprezentującego tablicę bajtów. Ten obiekt danych przychodzących zazwyczaj nie jest implementowany przez EE. Jednak obiekt zwracany przez tę metodę jest zawsze implementowany przez EE, który umożliwia EE implementowania `IEEDataStorage` interfejsu na cokolwiek klasy jest pożądane.

 Należy zauważyć, że dane `IEEDataStorage` dostarczane przez obiekt przychodzący `IEEDataStorage` muszą być takie same dane w obiekcie wychodzącym.

## <a name="see-also"></a>Zobacz też
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
