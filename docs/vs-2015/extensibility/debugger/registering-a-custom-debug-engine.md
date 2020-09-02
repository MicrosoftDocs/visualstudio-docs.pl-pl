---
title: Rejestrowanie niestandardowego aparatu debugowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9cf06e881034b980b8e40e095779007b3c7fa6f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703603"
---
# <a name="registering-a-custom-debug-engine"></a>Rejestrowanie niestandardowego aparatu debugowania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aparat debugowania musi zarejestrować się jako fabrykę klas w ramach Konwencji COM, a także zarejestrować się w programie Visual Studio za pomocą podklucza rejestru programu Visual Studio.  
  
> [!NOTE]
> Przykład sposobu rejestrowania aparatu debugowania można znaleźć w przykładzie textinterpretera, który jest zbudowany jako część [samouczka: kompilowanie aparatu debugowania przy użyciu biblioteki ATL com](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Proces serwera DLL  
 Zwykle aparat debugowania jest implementowany we własnej bibliotece DLL jako serwer COM. Oznacza to, że aparat debugowania musi zarejestrować identyfikator CLSID fabryki klas z modelem COM, aby program Visual Studio mógł uzyskać do niego dostęp. Następnie aparat debugowania musi się zarejestrować w programie Visual Studio, aby ustalić wszystkie właściwości (nazywane metrykami) obsługiwane przez aparat debugowania. Wybór metryk, które są zapisywane w podkluczu rejestru programu Visual Studio dla aparatu debugowania, zależy od funkcji obsługiwanych przez aparat debugowania.  
  
 [Narzędzia zestawu SDK do debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) opisują nie tylko lokalizacje rejestru niezbędne do zarejestrowania aparatu debugowania. opisano w nim również bibliotekę dbgmetric. lib, która zawiera wiele przydatnych funkcji i deklaracji dla deweloperów języka C++, które ułatwiają manipulowanie rejestrem.  
  
### <a name="example"></a>Przykład  
 Poniżej przedstawiono typowy przykład (z przykładu TextInterpreter), w którym pokazano, jak używać `SetMetric` funkcji (z dbgmetric. lib), aby zarejestrować aparat debugowania w programie Visual Studio. Przesyłane metryki są również zdefiniowane w dbgmetric. lib.  
  
> [!NOTE]
> TextInterpreter to podstawowy aparat debugowania; nie implementuje — i w związku z tym nie rejestruje — żadnych innych funkcji. Bardziej kompletny aparat debugowania będzie miał pełną listę `SetMetric` wywołań lub ich odpowiedniki, po jednym dla każdej funkcji obsługiwanej przez aparat debugowania.  
  
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
 [Tworzenie niestandardowego aparatu debugowania](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Pomocnicy zestawu SDK na potrzeby debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Samouczek: kompilowanie aparatu debugowania przy użyciu biblioteki ATL COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)
