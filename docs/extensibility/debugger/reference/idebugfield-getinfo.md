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
ms.openlocfilehash: 96ce3c428785bd6b817cb8ce0f97f14a87180d0c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62873889"
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

#### <a name="parameters"></a>Parametry
 `dwFields`

 [in] Kombinacji [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) stałych, które wybierze informacje mogą być wyświetlane. Jeśli pole reprezentuje symbol, jest to zazwyczaj nazwy symbolu i typu.

 `pFieldInfo`

 [out] Zwraca informacje w podanym [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struktury.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)