---
title: 'IDebugEnumField:: GetValueFromString | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77cce7a6780c816fbee0ade1c795cb1174e3e7f0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933456"
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
podczas Ciąg określający nazwę, dla której ma zostać pobrana wartość. Należy pamiętać, że w przypadku języka C++ jest to ciąg znaków dwubajtowych.

`pValue`\
określoną Zwraca skojarzoną wartość liczbową.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca `S_FALSE` , jeśli nazwa nie jest częścią wyliczenia lub kod błędu.

## <a name="remarks"></a>Uwagi
 W tej metodzie jest rozróżniana wielkość liter. Jeśli jest wymagana funkcja wyszukiwania bez uwzględniania wielkości liter (na przykład w języku, takim jak Visual Basic, gdzie nazwy nie są rozróżniane wielkości liter), należy użyć [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).

## <a name="see-also"></a>Zobacz też
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
