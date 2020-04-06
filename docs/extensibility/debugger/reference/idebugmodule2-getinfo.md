---
title: IDebugModule2::GetInfo | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c68c583702d7def5a7bff3ee40a9b8b2c537bb31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726962"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
Pobiera informacje o tym module.

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
[w] Kombinacja flag z wyliczenia [MODULE_INFO_FIELDS,](../../../extensibility/debugger/reference/module-info-fields.md) które określają, które pola `pInfo` mają być wypełnione.

`pInfo`\
[w, na zewnątrz] Struktura [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) wypełniona opisem modułu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 [Struktura MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) zawiera nazwę modułu, który jest wyświetlany w oknie **Moduły.**

## <a name="see-also"></a>Zobacz też
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
