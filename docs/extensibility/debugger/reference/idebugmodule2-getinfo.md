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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fe5060f66c56a033fb0bdcc8ae7dee368d2824e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323971"
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

## <a name="parameters"></a>Parametry
`dwFields`\
[in] Kombinacja flag z [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) wyliczenie określające pola, które z `pInfo` są wypełnione.

`pInfo`\
[out w] A [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) strukturę, która jest wypełniane opis modułu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struktura zawiera nazwę modułu, która jest wyświetlana w **modułów** okna.

## <a name="see-also"></a>Zobacz także
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)