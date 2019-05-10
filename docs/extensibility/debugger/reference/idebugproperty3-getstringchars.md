---
title: IDebugProperty3::GetStringChars | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 21ae1d4c16ce422d2baed2bd71ab5d0aa8b92e0c
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457666"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Pobiera parametry skojarzone z tą właściwością i zapisuje go w buforze dostarczone przez użytkownika.

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

 [in] Maksymalna liczba znaków, które może przechowywać buforu dostarczone przez użytkownika.

`rgString`\

 [out] Zwraca ciąg.

 [C++ tylko], `rgString` to wskaźnik do buforu, który otrzymuje z ciągu znaków Unicode. Tego buforu musi wynosić co najmniej `buflen` rozmiar znaków (nie w bajtach).

`pceltFetched`\

 [out] Gdzie jest zwracana liczba znaków rzeczywiście jest przechowywana w buforze. (Może być `NULL` w języku C++.)

## <a name="return-value"></a>Wartość zwracana
Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
W języku C++, należy uważać, aby mieć pewność, że rozmiar buforu jest co najmniej `buflen` znaków Unicode. Należy pamiętać, że znak Unicode 2 bajtów.

> [!NOTE]
> W języku C++ zwracanego ciągu nie obejmuje kończącego znaku null. Jeśli określony, `pceltFetched` określą liczbę znaków w ciągu.

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
