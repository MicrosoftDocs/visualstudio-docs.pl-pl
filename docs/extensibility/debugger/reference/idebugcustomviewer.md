---
title: IDebugCustomViewer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer
helpviewer_keywords:
- IDebugCustomViewer interface
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c576de860183353831eb9cc33293ead11123c59
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56700162"
---
# <a name="idebugcustomviewer"></a>IDebugCustomViewer
Ten interfejs umożliwia ewaluatora wyrażeń (EE), aby wyświetlić wartości właściwości w dowolnych format jest konieczne.

## <a name="syntax"></a>Składnia

```
IDebugCustomViewer : IUknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
EE implementuje ten interfejs, aby wyświetlić wartości właściwości w niestandardowym formacie.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Wywołania modelu COM `CoCreateInstance` funkcja tworzy wystąpienie tego interfejsu. `CLSID` Przekazany do `CoCreateInstance` są uzyskiwane z rejestru. Wywołanie [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) uzyskuje lokalizacji w rejestrze. Aby uzyskać szczegółowe informacje, jak również w przykładzie, zobacz uwagi.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
Ten interfejs implementuje następującą metodę:

|Metoda|Opis|
|------------|-----------------|
|[DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Nie, niezależnie od rodzaju jest niezbędne do wyświetlania danej wartości.|

## <a name="remarks"></a>Uwagi
Ten interfejs jest używany, gdy wartość właściwości nie można wyświetlić w normalny sposób — na przykład z tabeli danych lub inny typ właściwość typu złożonego. Przeglądarka niestandardowa, reprezentowane przez `IDebugCustomViewer` interfejsu, różni się od typu wizualizatora, czyli programu zewnętrznego do wyświetlania danych określonego typu, niezależnie od tego, EE. EE implementuje podglądu niestandardowego, które są specyficzne dla tego EE. Użytkownik wybierze typ wizualizatora do użycia, Wizualizator typów i Przeglądarka niestandardowa. Zobacz [Visualizing i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md) Aby uzyskać szczegółowe informacje na temat tego procesu.

Przeglądarka niestandardowa jest zarejestrowany w taki sam sposób jak EE i dlatego wymagają języka identyfikator GUID i identyfikator GUID dostawcy. Dokładne metryki (lub nazwę wpisu rejestru) znanego tylko EE. Ta metryka jest zwracany w [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) struktury, która z kolei jest zwracany przez wywołanie [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md). Jest wartością przechowywaną w metryce `CLSID` przekazana do modelu COM `CoCreateInstance` funkcji (Zobacz przykład).

[Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) funkcji `SetEEMetric`, może służyć do rejestrowania podglądu niestandardowego. W sekcji "Ewaluatory wyrażeń" rejestru `Debugging SDK Helpers` dla określonego rejestru kluczy, które wymaga podglądu niestandardowego. Należy pamiętać, że przeglądarka niestandardowa wymaga tylko jedną metrykę, (który jest definiowany przez implementujący EE) ewaluatora wyrażeń wymaga kilku predefiniowane metryki.

Normalnie, Przeglądarka niestandardowa udostępnia widok tylko do odczytu danych, ponieważ [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfejs dostarczony do [się pozycje DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) nie ma żadnych metod w przypadku zmiany wartości właściwości z wyjątkiem jako ciąg. Aby można było obsługiwać, zmieniając dowolne bloki danych, EE implementuje niestandardowy interfejs na ten sam obiekt, który implementuje `IDebugProperty3` interfejsu. Ten niestandardowy interfejs będzie dostarczać metody stosowane do zmiany dowolnego bloku danych.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Przykład
W tym przykładzie pokazano, jak można pobrać pierwszy Przeglądarka niestandardowa z właściwością, jeśli ta właściwość ma wszelkich przeglądarek niestandardowych.

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
