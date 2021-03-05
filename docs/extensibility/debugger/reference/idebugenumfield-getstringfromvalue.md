---
description: Ta metoda uzyskuje nazwę stałej wyliczenia z uwzględnieniem jej wartości.
title: 'IDebugEnumField:: GetStringFromValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8601be6a1c87fcad10c6e5260e791fcf2ce42f01
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153342"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Ta metoda uzyskuje nazwę stałej wyliczenia z uwzględnieniem jej wartości.

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
podczas Wartość, dla której ma zostać pobrana nazwa stałej wyliczenia.

`pbstrValue`\
określoną Zwraca nazwę stałej wyliczenia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` wartość, jeśli nie ma skojarzonej nazwy lub zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli istnieje więcej niż jedna nazwa skojarzona z tą samą wartością, zostanie zwrócona Pierwsza nazwa zdefiniowana w wyliczeniu.

## <a name="see-also"></a>Zobacz też
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
