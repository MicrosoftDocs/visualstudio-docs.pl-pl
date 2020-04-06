---
title: IDebugSettingsCallback2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c85b54f92970dca5d712b827019300f850b03cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719938"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Umożliwia aparatom debugowania zdalne odczytywanie ustawień metryki.

## <a name="syntax"></a>Składnia

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
Ten interfejs jest implementowany przez wywołanie zwrotne zdarzeń menedżera debugowania sesji i używane przez aparaty debugowania. Może być również używany lokalnie zamiast Dbgmetric[d]lib.

## <a name="methods"></a>Metody
W poniższej tabeli `IDebugSettingsCallback2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Wylicza dostępnych oceniających wyrażenie, biorąc pod uwagę identyfikatory języka i dostawcy.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Pobiera obiekt lokalny oceniający wyrażenie, biorąc pod uwagę metrykę.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Pobiera wartość, która odpowiada określonej metryki oceniającego wyrażenie.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Pobiera plik metryki oceniającego wyrażenie, podana nazwa lub metryka.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Pobiera unikatowy identyfikator dla metryki oceniającego wyrażenie, biorąc pod uwagę jego nazwę.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Pobiera ciąg wartości metryki oceniającego wyrażenie, biorąc pod uwagę jego nazwę.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Pobiera wartość metryki, biorąc pod uwagę jego nazwę.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Pobiera unikatowy identyfikator metryki, biorąc pod uwagę jego nazwę.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Pobiera ciąg wartości metryki, biorąc pod uwagę jego nazwę.|

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Przykład
Poniższy przykład pokazuje funkcję, która przyjmuje **IDebugSettingsCallback2** obiektu jako parametr.

```cpp
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)
{
    HRESULT hRes = E_FAIL;

    if ( ppCallback )
    {
        if ( EVAL(m_pdec) )
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```
