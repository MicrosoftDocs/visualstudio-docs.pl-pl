---
title: 'IPropertyProxyEESide:: replacementobject | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715037"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Tworzy kopię obiektu danych specyficzną dla ewaluatora wyrażeń (EE).

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
podczas Obiekt [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) przechowujący dane, które mają zostać skopiowane.

`dataOut`\
określoną Zwraca nowy `IEEDataStorage` obiekt.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 W tej metodzie jest przyznany obiekt [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) reprezentujący tablicę bajtów. Ten obiekt danych przychodzących zazwyczaj nie jest implementowany przez EE. Jednak obiekt zwrócony przez tę metodę jest zawsze zaimplementowany przez EE, co umożliwia implementację `IEEDataStorage` interfejsu na dowolnej klasie.

 Należy pamiętać, że dane dostarczane przez obiekt przychodzący `IEEDataStorage` muszą być tymi samymi danymi w obiekcie wychodzącym `IEEDataStorage` .

## <a name="see-also"></a>Zobacz też
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
