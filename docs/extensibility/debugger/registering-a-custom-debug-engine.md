---
title: Rejestrowanie niestandardowego aparatu debugowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe6fb916810bc8a7e960a4723a6a7c7a6f0c1410
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713221"
---
# <a name="register-a-custom-debug-engine"></a>Rejestrowanie niestandardowego aparatu debugowania
Aparat debugowania musi zarejestrować się jako fabryka klas, zgodnie z konwencjami COM, a także zarejestrować się w programie Visual Studio za pośrednictwem podklucza rejestru programu Visual Studio.

> [!NOTE]
> Przykład sposobu rejestrowania aparatu debugowania można znaleźć w przykładzie TextInterpreter, który jest zbudowany w ramach [samouczka: Tworzenie aparatu debugowania przy użyciu ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24).

## <a name="dll-server-process"></a>Proces serwera DLL
 Aparat debugowania jest zazwyczaj łączona we własnej biblioteki DLL jako serwer COM. W związku z tym aparat debugowania musi zarejestrować CLSID swojej fabryki klasy z COM przed Visual Studio może uzyskać do niego dostęp. Następnie aparat debugowania musi zarejestrować się w programie Visual Studio, aby ustanowić wszelkie właściwości (inaczej znane jako metryki) obsługuje aparat debugowania. Wybór metryk zapisanych w podkluczu rejestru programu Visual Studio zależy od funkcji, które obsługuje aparat debugowania.

 [Pomocników SDK do debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) opisuje nie tylko lokalizacje rejestru niezbędne do zarejestrowania aparatu debugowania; Opisano również *dbgmetric.lib* biblioteki, która zawiera szereg przydatnych funkcji i deklaracji dla deweloperów języka C++, które ułatwiają manipulowanie rejestru.

### <a name="example"></a>Przykład
 Poniższy przykład (z textinterpreter przykład) pokazuje, jak używać `SetMetric` funkcji (z *dbgmetric.lib*), aby zarejestrować aparat debugowania w programie Visual Studio. Przekazywane metryki są również definiowane w *pliku dbgmetric.lib*.

> [!NOTE]
> TextInterpreter jest podstawowym aparatem debugowania; nie jest skonfigurowany i dlatego nie rejestruje żadnych innych funkcji. Bardziej kompletny aparat debugowania będzie `SetMetric` miał całą listę wywołań lub ich odpowiednik, po jednym dla każdej funkcji obsługują aparat debugowania.

```
// Define base registry subkey to Visual Studio.
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";

HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)
{
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);

    return base::RegisterServer(bRegTypeLib, pCLSID);
}
```

## <a name="see-also"></a>Zobacz też
- [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [Pomocnicy SDK do debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Samouczek: Tworzenie aparatu debugowania przy użyciu ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)
