---
title: IDebugPortSupplierLocale2::SetLocale | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2::SetLocale
ms.assetid: 21e88510-caac-405e-ba45-cb00e19a28bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e366554858372f9e479f494d2bd419ebb9b2215
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202775"
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