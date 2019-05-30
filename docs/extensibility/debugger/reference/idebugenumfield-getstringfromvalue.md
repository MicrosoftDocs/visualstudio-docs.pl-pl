---
title: IDebugEnumField::GetStringFromValue | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd7466e5390cff747532dca0343680cf359db46a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345084"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Ta metoda uzyskuje nazwę danego jej wartość stałej wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetStringFromValue(
   ULONGLONG value,
   BSTR*     pbstrValue
);
```

```csharp
int GetStringFromValue(
   ulong      value,
   out string pbstrValue
);
```

## <a name="parameters"></a>Parametry
`value`\
[in] Wartość, dla którego należy pobrać nazwę wyliczenia stałej.

`pbstrValue`\
[out] Zwraca nazwę stała wyliczenia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` Jeśli wartość nie ma skojarzonego nazwy lub zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli istnieje więcej niż jedną nazwę skojarzonej z taką samą wartość, zostanie zwrócony imię zdefiniowane w wyliczeniu.

## <a name="see-also"></a>Zobacz także
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)