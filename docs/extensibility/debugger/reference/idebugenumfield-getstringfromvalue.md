---
title: IDebugEnumField::GetStringFromValue | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 25becdae62dbdda78e04404528eeb099a4914265
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212392"
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