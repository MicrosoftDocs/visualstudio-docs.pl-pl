---
title: IDebugEnumField::GetValueFromStringCaseInsensitive | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 551945ded9d1ba3e973f18c21463a896cbd478c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730252"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Ta metoda używa wyszukiwania bez uwzględniania wielkości liter, aby zwrócić wartość skojarzoną z nazwą stałej wyliczenia.

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
[w] Ciąg określający nazwę, dla której ma zostać określona wartość. Należy zauważyć, że w przypadku języka C++jest to ciąg znaków szeroki.

`pValue`\
[na zewnątrz] Zwraca skojarzoną wartość liczbową.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym `S_FALSE`razie zwraca , jeśli nazwa nie jest częścią wyliczenia lub kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest niewrażliwa na argumenty. Jeśli potrzebne jest wyszukiwanie z uwzględnieniem wielkości liter (na przykład w języku takim jak C++, w którym rozróżniana jest wielkość liter), należy użyć [pliku GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).

## <a name="see-also"></a>Zobacz też
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
