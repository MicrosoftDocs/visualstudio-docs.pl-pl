---
description: Umożliwia aparatom debugowania zdalne odczytywanie ustawień metryki.
title: IDebugSettingsCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 58e9ddfd3789fcfe7d81348714a8de2add743090
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071197"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
Umożliwia aparatom debugowania zdalne odczytywanie ustawień metryki.

## <a name="syntax"></a>Składnia

```
IDebugSettingsCallback2D : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
Ten interfejs jest implementowany przez wywołanie zwrotne zdarzenia Menedżera debugowania sesji i używane przez aparaty debugowania. Można go również użyć lokalnie zamiast dbgmetric [d]. lib.

## <a name="methods"></a>Metody
W poniższej tabeli przedstawiono metody `IDebugSettingsCallback2` .

|Metoda|Opis|
|------------|-----------------|
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Wylicza dostępne oceny wyrażeń z uwzględnieniem identyfikatorów języka i dostawcy.|
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Pobiera obiekt lokalny ewaluatora wyrażeń, który ma daną metrykę.|
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Pobiera wartość odpowiadającą określonej metryce ewaluatora wyrażeń.|
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Pobiera plik metryki ewaluatora wyrażeń, używając nazwy lub metryki.|
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Pobiera unikatowy identyfikator metryki Ewaluatora wyrażenia z nazwą.|
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Pobiera ciąg wartości metryki Ewaluatora wyrażenia z daną nazwą.|
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Pobiera wartość metryki pod nazwą.|
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Pobiera unikatowy identyfikator metryki o nazwie.|
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Pobiera ciąg wartości metryki o nazwie.|

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Przykład
W poniższym przykładzie pokazano funkcję, która przyjmuje obiekt **IDebugSettingsCallback2** jako parametr.

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
