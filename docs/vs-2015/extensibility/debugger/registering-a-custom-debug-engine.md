---
title: Rejestrowanie niestandardowego aparat debugowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8ce7faf0ad538478d3291b48ac7306a39558663b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732650"
---
# <a name="registering-a-custom-debug-engine"></a>Rejestrowanie niestandardowego aparatu debugowania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aparat debugowania musi zarejestrować się jako fabryki klas z konwencjami COM także zarejestrować przy użyciu programu Visual Studio za pomocą podklucza rejestru programu Visual Studio.  
  
> [!NOTE]
>  Przykładowy sposób rejestrowania aparat debugowania można znaleźć w tym przykładzie TextInterpreter powstała jako część [samouczek: tworzenie Debuguj aparat przy użyciu biblioteki ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Proces serwera biblioteki DLL  
 Zazwyczaj aparat debugowania jest wdrażany w jego własnej biblioteki DLL jako serwera COM. Oznacza to, że aparat debugowania należy zarejestrować identyfikator CLSID jego fabryki klas z modelem COM programu Visual Studio do niego dostęp. Następnie aparat debugowania musi zarejestrować się przy użyciu programu Visual Studio w celu ustanowienia żadnych właściwości (w przeciwnym razie znane jako metryki) debugowania aparatu obsługuje. Wybór metryki, które są zapisywane w podkluczu rejestru programu Visual Studio dla aparatu debugowania zależy od funkcje, które obsługuje aparatu debugowania.  
  
 [Pomocnicy zestawu SDK do debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) opisuje nie tylko w lokalizacji rejestru należy zarejestrować aparatu debugowania; biblioteki dbgmetric.lib, która zawiera wiele przydatnych funkcji i deklaracje dla deweloperów C++, które opisano również manipulowanie łatwiejsze rejestru.  
  
### <a name="example"></a>Przykład  
 Oto typowy przykład (z próbki TextInterpreter) przedstawiający sposób użycia `SetMetric` funkcji (od dbgmetric.lib), aby zarejestrować aparatu debugowania za pomocą programu Visual Studio. Metryki są przekazywane są również określone w dbgmetric.lib.  
  
> [!NOTE]
>  TextInterpreter to aparat debugowania podstawowego; nie implementuje — i dlatego nie rejestruje — inne funkcje. Bardziej kompletny aparat debugowania miałby całą listę `SetMetric` wywołania lub ich odpowiednika obsługuje jeden dla każdej funkcji aparatu debugowania.  
  
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
 [Pomocnicy zestawu SDK do debugowania](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Samouczek: Tworzenie aparatu debugowania, korzystając z modelu COM ATL](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)

