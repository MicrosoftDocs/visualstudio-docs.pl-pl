---
description: Pobiera ciąg skojarzony z tą właściwością i zapisuje go w buforze dostarczonym przez użytkownika.
title: 'IDebugProperty3:: GetStringChars | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d3b220fa02809015d1fa699c5e9eb5edac8cf2f3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166687"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Pobiera ciąg skojarzony z tą właściwością i zapisuje go w buforze dostarczonym przez użytkownika.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetStringChars(
    ULONG  buflen,
    WCHAR* rgString,
    ULONG* pceltFetched
);
```

```csharp
int GetStringChars(
    uint       buflen,
    out string rgString,
    out uint   pceltFetched
);
```

## <a name="parameters"></a>Parametry
`buflen`\
podczas Maksymalna liczba znaków, jaką może zawierać bufor dostarczony przez użytkownika.

`rgString`\
określoną Zwraca ciąg.

 [Tylko C++], `rgString` jest wskaźnikiem do buforu, który odbiera znaki Unicode ciągu. Rozmiar buforu musi wynosić co najmniej `buflen` znaków (nie bajtów).

`pceltFetched`\
określoną Miejsce, w którym zwracana jest liczba znaków faktycznie przechowywanych w buforze. (Może być `NULL` w języku C++).

## <a name="return-value"></a>Wartość zwracana
Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
W języku C++ należy zwrócić uwagę, aby upewnić się, że bufor ma co najmniej `buflen` znaki Unicode. Należy zauważyć, że znak Unicode ma długość 2 bajtów.

> [!NOTE]
> W języku C++ zwrócony ciąg nie zawiera kończącego znaku null. Jeśli jest podany, `pceltFetched` określi liczbę znaków w ciągu.

## <a name="example"></a>Przykład

```cpp
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)
{
    CStringW returnString = L"";
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;
    If (pProp3 != NULL) {
        ULONG dwStrLen = 0;
        HRESULT hr;
        hr = pProp3->GetStringCharLength(&dwStrLen);
        if (SUCCEEDED(hr) && dwStrLen > 0) {
            ULONG dwRead;
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);
            hr = pProp3->GetStringChars(dwStrLen,
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),
                                        &dwRead);
        }
    }
    return(returnString);
}
```

## <a name="see-also"></a>Zobacz także
- [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
