---
title: IDebugField::GetInfo | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 53c0de1b956202f95b4995855ec5bdda0ebe59d3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352627"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
Ta metoda pobiera zawiera informacje o polu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetInfo( 
   FIELD_INFO_FIELDS dwFields,
   FIELD_INFO* pFieldInfo
);
```

```csharp
int GetInfo(
   enum_FIELD_INFO_FIELDS dwFields,
   FIELD_INFO[] pFieldInfo
);
```

## <a name="parameters"></a>Parametry
`dwFields`\
[in] Kombinacji [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) stałych, które wybierze informacje mogą być wyświetlane. Jeśli pole reprezentuje symbol, jest to zazwyczaj nazwy symbolu i typu.

`pFieldInfo`\
[out] Zwraca informacje w podanym [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struktury.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)