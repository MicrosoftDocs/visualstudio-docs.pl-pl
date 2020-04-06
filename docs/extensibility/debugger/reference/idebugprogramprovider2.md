---
title: Program IDebugProvider2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 43557e5d81e5140967a1189e57a350595d0f7220
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721690"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Ten zarejestrowany interfejs umożliwia menedżerowi debugowania sesji (SDM) uzyskanie informacji o programach, które zostały "opublikowane" za pośrednictwem interfejsu [IDebugProgramPublisher2.](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)

## <a name="syntax"></a>Składnia

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
Aparat debugowania (DE) implementuje ten interfejs, aby zapewnić informacje o programach są debugowane. Ten interfejs jest zarejestrowany w sekcji DE rejestru `metricProgramProvider`przy użyciu metryki, zgodnie z opisem w [SDK Pomocników debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Wywołanie `CoCreateInstance` funkcji COM `CLSID` z dostawcą programu, który jest uzyskiwany z rejestru. Zobacz przykład.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable

|Metoda|Opis|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Uzyskuje informacje o uruchomionych programach, filtrowanych na różne sposoby.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Pobiera węzeł programu, biorąc pod uwagę określony identyfikator procesu.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Ustanawia wywołanie zwrotne do obserwowanie zdarzeń dostawcy skojarzonych z określonymi rodzajami procesów.|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Ustanawia ustawienia regionalne dla wszelkich zasobów specyficznych dla języka potrzebnych przez DE.|

## <a name="remarks"></a>Uwagi
Zwykle proces używa tego interfejsu, aby dowiedzieć się o programach uruchomionych w tym procesie.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

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

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [Pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
