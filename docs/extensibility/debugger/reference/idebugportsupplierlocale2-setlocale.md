---
title: IDebugPortSupplierLocale2::SetLocale | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2::SetLocale
ms.assetid: 21e88510-caac-405e-ba45-cb00e19a28bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 72e662060067f455275465ce4ade7ed824936313
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353287"
---
# <a name="idebugportsupplierlocale2setlocale"></a>IDebugPortSupplierLocale2::SetLocale
Ustawia ustawienia regionalne dla dostawcy portu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetLocale(
   WORD wLangID
);
```

```csharp
int SetLocale(
   ushort wLangID
);
```

## <a name="parameters"></a>Parametry
`wLangID`\
Identyfikator ustawień regionalnych ustawić.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugPortSupplierLocale2](../../../extensibility/debugger/reference/idebugportsupplierlocale2.md)