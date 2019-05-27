---
title: IDebugField::GetInfo | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3d28db6824afe6230cc8e00fae8e144dc541af59
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212195"
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