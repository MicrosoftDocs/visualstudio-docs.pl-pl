---
description: Ten interfejs umożliwia ewaluatora wyrażeń (EE) wyświetlanie wartości właściwości w dowolnym formacie.
title: IDebugCustomViewer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3c44706549d7d638a8fbf3686de57780ffa6bf4e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077554"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Ten interfejs umożliwia ewaluatora wyrażeń (EE) wyświetlanie wartości właściwości w dowolnym formacie.

## <a name="syntax"></a>Składnia

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
W programie EE jest implementowany ten interfejs umożliwiający wyświetlenie wartości właściwości w formacie niestandardowym.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Wywołanie `CoCreateInstance` funkcji com tworzy wystąpienie tego interfejsu. `CLSID`Przesłany do `CoCreateInstance` jest uzyskiwany z rejestru. Wywołanie [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) umożliwia uzyskanie lokalizacji w rejestrze. Zobacz uwagi, aby uzyskać szczegółowe informacje, a także przykład.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
Ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Jest to konieczne, aby wyświetlić daną wartość.|

## <a name="remarks"></a>Uwagi
Ten interfejs jest używany, gdy wartość właściwości nie może być wyświetlana w zwykły sposób — na przykład z tabelą danych lub innym typem złożonej właściwości. Niestandardowa przeglądarka, reprezentowana przez `IDebugCustomViewer` interfejs, różni się od wizualizatora typu, który jest zewnętrznym programem do wyświetlania danych określonego typu niezależnie od EE. Na stronie EE jest implementowana przeglądarka niestandardowa, która jest specyficzna dla tej EE. Użytkownik wybiera typ wizualizatora, który ma być używany, może być wizualizatorem typu lub podglądem niestandardowym. Zobacz [wizualizowanie i wyświetlanie danych,](../../../extensibility/debugger/visualizing-and-viewing-data.md) Aby uzyskać szczegółowe informacje na temat tego procesu.

Przeglądarka niestandardowa jest zarejestrowana w taki sam sposób jak w przypadku wersji EE, dlatego wymaga identyfikatora GUID języka i identyfikatora GUID dostawcy. Dokładna Metryka (lub nazwa wpisu rejestru) jest znana tylko dla EE. Ta Metryka jest zwracana w strukturze [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) , która z kolei jest zwracana przez wywołanie [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). Wartość przechowywana w metryce jest `CLSID` przenoszona do `CoCreateInstance` funkcji com (Zobacz przykład).

[Pomocników zestawu SDK dla funkcji debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , `SetEEMetric` mogą służyć do rejestrowania niestandardowych podglądów. Zapoznaj się z sekcją rejestru "oceny wyrażeń" `Debugging SDK Helpers` w temacie dotyczącym określonych kluczy rejestru wymaganych przez przeglądarkę niestandardową. Należy zauważyć, że Podgląd niestandardowy wymaga tylko jednej metryki (zdefiniowanej przez realizatora EE), podczas gdy ewaluatora wyrażeń wymaga kilku wstępnie zdefiniowanych metryk.

Zwykle przeglądarka niestandardowa udostępnia widok danych tylko do odczytu, ponieważ interfejs [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) dostarczany do [DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) nie ma metod zmieniania wartości właściwości z wyjątkiem ciągu. Aby można było obsłużyć zmianę dowolnych bloków danych, program EE implementuje interfejs niestandardowy na tym samym obiekcie, który implementuje `IDebugProperty3` interfejs. W tym interfejsie niestandardowym można następnie udostępnić metody umożliwiające zmianę dowolnego bloku danych.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Przykład
Ten przykład pokazuje, jak pobrać pierwszą niestandardową przeglądarkę z właściwości, jeśli ta właściwość ma jakiekolwiek niestandardowe osoby przeglądające.

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
