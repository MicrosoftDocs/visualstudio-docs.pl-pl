---
title: IDebugProperty3::GetStringChars | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 693a29bc30ef206428713ace36275389de1b7f0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721082"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Pobiera ciąg skojarzony z tą właściwością i przechowuje go w buforze dostarczonym przez użytkownika.

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
[w] Maksymalna liczba znaków, które może pomieścić bufor dostarczony przez użytkownika.

`rgString`\
[na zewnątrz] Zwraca ciąg.

 [C++ tylko], `rgString` jest wskaźnikiem do buforu, który odbiera znaki Unicode ciągu. Ten bufor musi `buflen` mieć rozmiar co najmniej znaków (nie bajtów).

`pceltFetched`\
[na zewnątrz] Gdzie zwracana jest liczba znaków faktycznie przechowywanych w buforze. (Może `NULL` być w języku C++.)

## <a name="return-value"></a>Wartość zwracana
Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
W języku C++, należy zwrócić uwagę, aby zapewnić, że bufor jest co `buflen` najmniej znaków Unicode długo. Należy zauważyć, że znak Unicode ma 2 bajty długości.

> [!NOTE]
> W języku C++ zwrócony ciąg nie zawiera kończącego się znaku null. Jeśli podano, `pceltFetched` określi liczbę znaków w ciągu.

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

## <a name="see-also"></a>Zobacz też
- [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
