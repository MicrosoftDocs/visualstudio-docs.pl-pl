---
title: Pobieranie właściwości lokalnych | Microsoft Docs
description: Dowiedz się, w jaki sposób program Visual Studio używa EnumChildren do uzyskiwania lokalnych właściwości z tymi przykładami dla kodu zarządzanego i niezarządzanego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, getting local properties
- debugging [Debugging SDK], local properties
- expression evaluation, local properties
ms.assetid: 6c3a79e8-1ba1-4863-97c3-0216c3d9f092
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17b6d104f88999ba7dd8e115a752a78853af6603
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560021"
---
# <a name="get-local-properties"></a>Pobierz właściwości lokalne
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz testerzy [wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzana próbnik wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Program Visual Studio wywołuje [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) , aby uzyskać obiekt [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) , który zapewnia dostęp do wszystkich elementów lokalnych, które mają być wyświetlane w oknie **zmiennych lokalnych** . Program Visual Studio następnie wywołuje polecenie [dalej](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) , aby uzyskać informacje do wyświetlenia dla każdego lokalnego. W tym przykładzie Klasa `CEnumPropertyInfo` implementuje `IEnumDebugPropertyInfo2` interfejs.

Ta implementacja programu `IEnumDebugPropertyInfo2::Next` wykonuje następujące zadania:

1. Czyści tablicę, w której mają być przechowywane informacje.

2. Wywołania [dalej](../../extensibility/debugger/reference/ienumdebugfields-next.md) dla każdego lokalnego, przechowując zwrócone [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) w tablicy, która ma zostać zwrócona. Obiekt [IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md) został dostarczony podczas `CEnumPropertyInfo` tworzenia wystąpienia tej klasy.

## <a name="managed-code"></a>Kod zarządzany
Ten przykład pokazuje implementację wartości `IEnumDebugPropertyInfo2::EnumChildren` lokalnych metody w kodzie zarządzanym.

```csharp
namespace EEMC
{
    public class CEnumMethodField : IEnumDebugFields
    {
        public HRESULT Next(
                uint                  count,
                DEBUG_PROPERTY_INFO[] properties,
            out uint                  fetched)
        {
            if (count > properties.Length)
                throw new COMException();

            // Zero out the array.
            for (int i= 0; i < count; i++)
            {
                properties[i].bstrFullName = "";
                properties[i].bstrName = "";
                properties[i].bstrType = "";
                properties[i].bstrValue = "";
                properties[i].dwAttrib = 0;
                properties[i].dwFields = 0;
                properties[i].pProperty = null;
            }
            fetched = 0;

            // COM interop.
            HRESULT hr;
            uint innerFetched;
            IDebugField[] field = new IDebugField[1];

            while (fetched < count)
            {
                field[0] = null;
                innerFetched = 0;

                // Get next field.
                if (fetched < fieldCount)
                    hr = fields.Next(1, field, ref innerFetched);
                // No more fields.
                else return COM.S_FALSE;

                if (hr != COM.S_OK || innerFetched != 1 || field[0] == null)
                    throw new COMException("CEnumPropertyInfo.Next");

                // Get property from field.
                CFieldProperty fieldProperty =
                        new CFieldProperty(provider, address, binder, field[0]);

                DEBUG_PROPERTY_INFO[] property =
                        new DEBUG_PROPERTY_INFO[1];
                fieldProperty.GetPropertyInfo((uint) infoFlags, radix, 0, null, 0, property);
                properties[fetched++] = property[0];
            }
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Kod niezarządzany
 Ten przykład pokazuje implementację wartości `IEnumDebugPropertyInfo2::EnumChildren` lokalnych metody w kodzie niezarządzanym.

```cpp
STDMETHODIMP CEnumPropertyInfo::Next(
    in  ULONG                count,
    out DEBUG_PROPERTY_INFO* pelements,
    out ULONG*               pfetched )
{
    if (pfetched)
        *pfetched = 0;
    if (!pelements)
        return E_INVALIDARG;
    else
        memset( pelements, 0, count * sizeof(DEBUG_PROPERTY_INFO));

    HRESULT hr  = S_OK;
    ULONG   idx = 0;
    while (idx < count)
    {
        ULONG        fetchedFields;
        IDebugField* pfield;

        //get the next field
        hr = m_fields->Next( 1, &pfield, &fetchedFields );
        if (FAILED(hr))
            return hr;
        if (fetchedFields != 1)
            return E_FAIL;
        idx++;

        //create a CFieldProperty to retrieve the DEBUG_PROPERTY_INFO
        CFieldProperty* pproperty =
            new CFieldProperty( m_provider, m_address, m_binder, pfield );
        pfield->Release();
        if (!pproperty)
            return E_OUTOFMEMORY;

        hr = pproperty->Init();
        if (FAILED(hr))
        {
            pproperty->Release();
            return hr;
        }

        hr = pproperty->GetPropertyInfo( m_infoFlags,
                                         m_radix,
                                         0,
                                         NULL,
                                         0,
                                         pelements + idx - 1);
        pproperty->Release();
        if (FAILED(hr))
            return hr;
    }

    if (pfetched)
        *pfetched = idx;
    return hr;
}
```

## <a name="see-also"></a>Zobacz także
- [Przykładowa implementacja elementów lokalnych](../../extensibility/debugger/sample-implementation-of-locals.md)
- [Wyliczanie zmiennych lokalnych](../../extensibility/debugger/enumerating-locals.md)
