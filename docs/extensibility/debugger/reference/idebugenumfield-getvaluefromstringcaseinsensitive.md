---
description: Ta metoda używa wyszukiwania bez uwzględniania wielkości liter do zwrócenia wartości skojarzonej z nazwą stałej wyliczenia.
title: 'IDebugEnumField:: GetValueFromStringCaseInsensitive | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f853598c5d3c9b293c806e1db475c5053a1a208e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153225"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Ta metoda używa wyszukiwania bez uwzględniania wielkości liter do zwrócenia wartości skojarzonej z nazwą stałej wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetValueFromStringCaseInsensitive(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromStringCaseInsensitive(
   string    pszValue,
   out ulong pValue
);
```

## <a name="parameters"></a>Parametry
`pszValue`\
podczas Ciąg określający nazwę, dla której ma zostać pobrana wartość. Należy pamiętać, że w przypadku języka C++ jest to ciąg znaków dwubajtowych.

`pValue`\
określoną Zwraca skojarzoną wartość liczbową.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` , jeśli nazwa nie jest częścią wyliczenia lub kod błędu.

## <a name="remarks"></a>Uwagi
 W tej metodzie nie jest rozróżniana wielkość liter. Jeśli jest wymagana funkcja wyszukiwania z uwzględnieniem wielkości liter (na przykład w języku C++, gdzie nazwy są rozróżniane wielkości liter), należy użyć [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).

## <a name="see-also"></a>Zobacz też
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
