---
title: IDebugSettingsCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 859522ebdbe231146c73b25c5e4c92fba9809727
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321939"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Włącza debugowanie aparatów odczytać ustawienia metryki zdalnie.

## <a name="syntax"></a>Składnia

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
Ten interfejs jest implementowany przez wywołanie zwrotne zdarzeń Menedżera sesji debugowania i używane przez aparaty debugowania. Jego można również lokalnie zamiast .lib Dbgmetric [d].

## <a name="methods"></a>Metody
W poniższej tabeli przedstawiono metody `IDebugSettingsCallback2`.

|Metoda|Opis|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Wylicza ewaluatory wyrażeń dostępne, biorąc pod uwagę identyfikatorów języka i dostawcy.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Pobiera wyrażenie ewaluatora lokalnego obiektu podane metryki.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Pobiera wartość, która odnosi się do określonej metryki Ewaluator wyrażeń.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Pobiera plik metryki ewaluatora wyrażenia, podana nazwa lub metrykę.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Pobiera unikatowy identyfikator dla metryki ewaluatora wyrażeń nadać jej nazwę.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Pobiera ciąg wartość metryki ewaluatora wyrażeń nadać jej nazwę.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Pobiera wartość metryki nadać jej nazwę.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Pobiera unikatowy identyfikator metryki nadać jej nazwę.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Pobiera ciąg wartość metryki nadać jej nazwę.|

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Przykład
W poniższym przykładzie pokazano funkcję, która przyjmuje **IDebugSettingsCallback2** obiektu jako parametr.

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
