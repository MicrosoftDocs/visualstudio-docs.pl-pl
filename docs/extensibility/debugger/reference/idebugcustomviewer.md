---
title: IDebugCustomViewer | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c44d2289180ece35725b9258e9d20abeb3a4cac3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732416"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Ten interfejs umożliwia oceniającemu wyrażenie (EE) wyświetlanie wartości właściwości w dowolnym formacie jest to konieczne.

## <a name="syntax"></a>Składnia

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
EE implementuje ten interfejs do wyświetlania wartości właściwości w formacie niestandardowym.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Wywołanie `CoCreateInstance` funkcji COM powoduje wystąpienia tego interfejsu. Przekazywane `CLSID` do `CoCreateInstance` uzyskuje się z rejestru. Wywołanie [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) uzyskuje lokalizację w rejestrze. Zobacz Uwagi, aby uzyskać szczegółowe informacje, a także przykład.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
Ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Czy wszystko, co jest niezbędne do wyświetlenia danej wartości.|

## <a name="remarks"></a>Uwagi
Ten interfejs jest używany, gdy wartość właściwości nie może być wyświetlana w zwykły sposób — na przykład z tabelą danych lub innym złożonym typem właściwości. Przeglądarka niestandardowa, reprezentowana `IDebugCustomViewer` przez interfejs, różni się od wizualizatora typu, który jest zewnętrznym programem do wyświetlania danych określonego typu, niezależnie od EE. EE implementuje niestandardową przeglądarkę, która jest specyficzna dla tego EE. Użytkownik wybiera typ wizualizatora do użycia, czy to wizualizator typu lub przeglądarki niestandardowej. Zobacz [wizualizacji i wyświetlania danych, aby](../../../extensibility/debugger/visualizing-and-viewing-data.md) uzyskać szczegółowe informacje na temat tego procesu.

Przeglądarka niestandardowa jest rejestrowana w taki sam sposób jak EE i dlatego wymaga identyfikatora GUID języka i identyfikatora GUID dostawcy. Dokładna metryka (lub nazwa wpisu rejestru) jest znana tylko ee. Ta metryka jest zwracana w [strukturze DEBUG_CUSTOM_VIEWER,](../../../extensibility/debugger/reference/debug-custom-viewer.md) która z kolei jest zwracana przez wywołanie [do GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). Wartość przechowywana w metryki jest `CLSID` przekazywana `CoCreateInstance` do funkcji COM (zobacz przykład).

[Pomocników SDK dla debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) funkcji, `SetEEMetric`można użyć do rejestracji przeglądarki niestandardowej. Zobacz sekcję rejestru "Oceniający `Debugging SDK Helpers` wyrażenia" dla określonych kluczy rejestru, których potrzebuje niestandardowa przeglądarka. Należy zauważyć, że niestandardowa przeglądarka potrzebuje tylko jednej metryki (zdefiniowanej przez realizatora EE), podczas gdy oceniający wyrażenie wymaga kilku wstępnie zdefiniowanych metryk.

Zwykle niestandardowa przeglądarka udostępnia widok tylko do odczytu danych, ponieważ interfejs [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) dostarczony do [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) nie ma metod zmiany wartości właściwości, z wyjątkiem ciągu. Aby obsługiwać zmiany dowolnych bloków danych, EE implementuje niestandardowy interfejs na `IDebugProperty3` tym samym obiekcie, który implementuje interfejs. Ten interfejs niestandardowy następnie zapewni metody potrzebne do zmiany dowolnego bloku danych.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Przykład
W tym przykładzie pokazano, jak uzyskać pierwszą przeglądarkę niestandardową z usługi, jeśli ta właściwość ma żadnych niestandardowych widzów.

```cpp
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)
{
    // This string is typically defined globally.  For this example, it
    // is defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugCustomViewer *pViewer = NULL;
    if (pProperty != NULL) {
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);
        if (pProperty3 != NULL) {
            HRESULT hr;
            ULONG viewerCount = 0;
            hr = pProperty3->GetCustomViewerCount(&viewerCount);
            if (viewerCount > 0) {
                ULONG viewersFetched = 0;
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };
                hr = pProperty3->GetCustomViewerList(0,
                                                     1,
                                                     &viewerInfo,
                                                     &viewersFetched);
                if (viewersFetched == 1) {
                    CLSID clsidViewer = { 0 };
                    CComPtr<IDebugCustomViewer> spCustomViewer;
                    // Get the viewer's CLSID from the registry.
                    ::GetEEMetric(viewerInfo.guidLang,
                                  viewerInfo.guidVendor,
                                  viewerInfo.bstrMetric,
                                  &clsidViewer,
                                  strRegistrationRoot);
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {
                        // Instantiate the custom viewer.
                        spCustomViewer.CoCreateInstance(clsidViewer);
                        if (spCustomViewer != NULL) {
                            pViewer = spCustomViewer.Detach();
                        }
                    }
                }
            }
        }
    }
    return(pViewer);
}
```

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
