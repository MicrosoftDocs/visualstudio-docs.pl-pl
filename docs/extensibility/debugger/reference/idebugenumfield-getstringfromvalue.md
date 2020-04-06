---
title: IDebugEnumField::GetStringFromValue | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5de59c573f7e233ea2aacb0dfa38826051c59373
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730289"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Ta metoda uzyskuje nazwę stałej wyliczenia, biorąc pod uwagę jego wartość.

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
[w] Wartość, dla której ma zostać nastawiła nazwę stałej wyliczenia.

`pbstrValue`\
[na zewnątrz] Zwraca nazwę stałej wyliczenia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym `S_FALSE` razie zwraca, jeśli wartość nie ma skojarzonej nazwy lub zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli istnieje więcej niż jedna nazwa skojarzona z tą samą wartością, zostanie zwrócona imię zdefiniowane w wyliczeniu.

## <a name="see-also"></a>Zobacz też
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
