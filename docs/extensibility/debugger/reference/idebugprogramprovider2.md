---
description: Ten zarejestrowany interfejs umożliwia menedżerowi debugowania sesji (SDM) uzyskanie informacji o programach opublikowanych za pomocą interfejsu IDebugProgramPublisher2.
title: IDebugProgramProvider2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5bead60e23c708d8a23fcd382b4db0f3f9f7e4c1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065245"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Ten zarejestrowany interfejs umożliwia menedżerowi debugowania sesji (SDM) uzyskanie informacji o programach, które zostały "opublikowane" za pomocą interfejsu [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) .

## <a name="syntax"></a>Składnia

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
Aparat debugowania (DE) implementuje ten interfejs, aby zapewnić informacje o debugowanych programach. Ten interfejs jest zarejestrowany w DE sekcji rejestru przy użyciu metryki `metricProgramProvider` , zgodnie z opisem w [pomocników zestawu SDK na potrzeby debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Wywoływanie `CoCreateInstance` funkcji com z `CLSID` dostawcą programu uzyskanym z rejestru. Zapoznaj się z przykładem.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych

|Metoda|Opis|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Uzyskuje informacje o uruchomionych programach, przefiltrowanych na różne sposoby.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Pobiera węzeł programu z określonym IDENTYFIKATORem procesu.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Ustanawia wywołanie zwrotne do śledzenia zdarzeń dostawcy skojarzonych z określonymi rodzajami procesów.|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Ustanawia ustawienia regionalne dla wszystkich zasobów specyficznych dla języka wymaganych przez DE.|

## <a name="remarks"></a>Uwagi
Zwykle proces korzysta z tego interfejsu, aby dowiedzieć się o programach uruchomionych w ramach tego procesu.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Przykład

```cpp
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)
{
    // This is typically defined globally. For this example, it is
    // defined here.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";
    IDebugProgramProvider2 *pProvider = NULL;
    if (pDebugEngineGuid != NULL) {
        CLSID clsidProvider = { 0 };
        ::GetMetric(NULL,
                    metrictypeEngine,
                    *pDebugEngineGuid,
                    metricProgramProvider,
                    &clsidProvider,
                    strRegistrationRoot);
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {
            CComPtr<IDebugProgramProvider2> spProgramProvider;
            spProgramProvider.CoCreateInstance(clsidProvider);
            if (spProgramProvider != NULL) {
                pProvider = spProgramProvider.Detach();
            }
        }
    }
    return(pProvider);
}
```

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
