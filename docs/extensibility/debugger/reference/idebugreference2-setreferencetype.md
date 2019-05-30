---
title: IDebugReference2::SetReferenceType | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetReferenceType
helpviewer_keywords:
- IDebugReference2::SetReferenceType
ms.assetid: 5854a172-ea82-481c-97d9-c7fc16923d44
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: add8a7c8243cd9754c30e38b5fac8fcf715a63da
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339834"
---
# <a name="idebugreference2setreferencetype"></a>IDebugReference2::SetReferenceType
Ustawia typ odwołania. Zarezerwowane do użytku w przyszłości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetReferenceType ( 
   REFERENCE_TYPE dwRefType
);
```

```csharp
int SetReferenceType ( 
   enum_REFERENCE_TYPE dwRefType
);
```

## <a name="parameters"></a>Parametry
`dwRefType`\
[in] Wartość z zakresu od [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) wyliczenie, który określa typ odwołania.

## <a name="return-value"></a>Wartość zwracana
 Zawsze zwraca `E_NOTIMPL`.

## <a name="see-also"></a>Zobacz także
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)