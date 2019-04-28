---
title: IDebugModule2::GetInfo | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0a5ad3d7651e89c2ef864a184155e8b0a430d79
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872734"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
Pobiera informacje na temat tego modułu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetInfo( 
   MODULE_INFO_FIELDS dwFields,
   MODULE_INFO*       pInfo
);
```

```cpp
int GetInfo( 
   enum_MODULE_INFO_FIELDS dwFields,
   MODULE_INFO[]           pInfo
);
```

#### <a name="parameters"></a>Parametry
 `dwFields`

 [in] Kombinacja flag z [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) wyliczenie określające pola, które z `pInfo` są wypełnione.

 `pInfo`

 [out w] A [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) strukturę, która jest wypełniane opis modułu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struktura zawiera nazwę modułu, która jest wyświetlana w **modułów** okna.

## <a name="see-also"></a>Zobacz też
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)