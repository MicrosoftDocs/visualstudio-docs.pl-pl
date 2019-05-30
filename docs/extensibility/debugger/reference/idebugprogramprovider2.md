---
title: IDebugProgramProvider2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6f392e823d28440a73a1aaa606351c28c6e9c70
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343361"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
Ten interfejs zarejestrowanych umożliwia debugowania sesji manager (SDM), aby uzyskać informacje na temat programów, które "opublikowano" za pośrednictwem [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) interfejsu.

## <a name="syntax"></a>Składnia

```
IDebugProgramProvider2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
Aparat debugowania (DE) implementuje ten interfejs w celu dostarczenia informacji o debugowane programy. Ten interfejs jest zarejestrowany w sekcji DE rejestru za pomocą metryk `metricProgramProvider`, zgodnie z opisem w [pomocnicy zestawu SDK do debugowania](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
Wywołania modelu COM `CoCreateInstance` funkcją `CLSID` dostawcy program, który jest uzyskiwana z rejestru. Zobacz przykład.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności

|Metoda|Opis|
|------------|-----------------|
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Uzyskuje informacje na temat programów, uruchamianie, przefiltrowane na różne sposoby.|
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Pobiera węzeł program podany identyfikator określonego procesu.|
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Określa wywołanie zwrotne do obserwacji zdarzenia dostawcy skojarzonego z określonego rodzaju procesy.|
|[SetLocale](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Określa ustawienia regionalne dla wszystkich zasobów specyficznych dla języka, wymagane przez DE.|

## <a name="remarks"></a>Uwagi
Zwykle proces używa tego interfejsu do tutaj znajdziesz informacje dotyczące programów uruchomionych w tym procesie.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

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
