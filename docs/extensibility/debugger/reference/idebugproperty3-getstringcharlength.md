---
description: Zwraca liczbę znaków w ciągu skojarzonej właściwości.
title: 'IDebugProperty3:: GetStringCharLength | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringCharLength
helpviewer_keywords:
- IDebugProperty3::GetStringCharLength
ms.assetid: 89a8676b-6da9-4358-91c2-039bf33f99e4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eaf0792b6e0c2311b7eeb01f12b01a485739c6c9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171386"
---
# <a name="idebugproperty3getstringcharlength"></a>IDebugProperty3::GetStringCharLength
Zwraca liczbę znaków w ciągu skojarzonej właściwości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetStringCharLength(
    ULONG *pLen
);
```

```csharp
int GetStringCharLength(
    out uint pLen
);
```

## <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`pLen`|określoną Zwraca liczbę znaków w ciągu właściwości.|

## <a name="return-value"></a>Wartość zwracana
Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
Zazwyczaj ta metoda jest używana jako preludium do alokowania buforu dla wywołania metody [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) .

## <a name="example"></a>Przykład
Poniższy przykład pokazuje, jak zaimplementować tę metodę dla obiektu **CProperty** , który uwidacznia Interfejs [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) .

```cpp
STDMETHODIMP CProperty::GetStringCharLength(ULONG *pLen)
{
    HRESULT hr = E_INVALIDARG;

    EVALFLAGS oldEVALFLAGS = m_EVALFLAGS;

    m_EVALFLAGS &= ~EVAL_NOFUNCEVAL;

    if (pLen)
    {
        DEBUG_PROPERTY_INFO dpInfo;
        dpInfo.bstrValue = NULL;
        ULONG ulen = 0;
        hr = GetPropertyInfo(DEBUGPROP_INFO_VALUE,10,DEFAULT_TIMEOUT,NULL,0,&dpInfo);
        if (hr == S_OK && dpInfo.bstrValue)
        {
            if (wcscmp(dpInfo.bstrValue,L"Nothing") == 0)
            {
                ulen = 0; //VSWhidbey#64815
            }
            else
            {
                ulen = ::SysStringLen(dpInfo.bstrValue);
                if( ulen > 2 &&
                    dpInfo.bstrValue[0] == L'"' &&
                    dpInfo.bstrValue[ulen-1] == L'"')
                {
                    ulen = ulen > 2 ? ulen - 2 : ulen; //remove two double quotes
                }
            }
        }
        ::SysFreeString(dpInfo.bstrValue);
        *pLen = ulen;
    }
    m_EVALFLAGS = oldEVALFLAGS;
    return hr;
}
```

## <a name="see-also"></a>Zobacz też
- [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
