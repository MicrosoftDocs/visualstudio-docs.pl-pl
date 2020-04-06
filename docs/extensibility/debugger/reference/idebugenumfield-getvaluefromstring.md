---
title: IDebugEnumField::GetValueFromString | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bb340721c9f446b740c2723dc3f6dc05452e74de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730261"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Ta metoda zwraca wartość skojarzoną z nazwą stałej wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetValueFromString(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromString(
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
 W tej metodzie rozróżniana jest wielkość liter. Jeśli potrzebne jest wyszukiwanie bez uwzględniania wielkości liter (na przykład w języku takim jak Visual Basic, w którym nazwy nie są uwzględniane wielkość liter), należy użyć [getvaluefromstringcaseinsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).

## <a name="see-also"></a>Zobacz też
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
