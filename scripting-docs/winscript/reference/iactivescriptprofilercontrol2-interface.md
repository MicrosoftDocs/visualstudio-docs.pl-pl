---
title: IActiveScriptProfilerControl2 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2 interface
ms.assetid: 89455276-5c23-420b-a7e0-804a32635291
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11987054ed934f4004333f136ea35696ff6c394f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993037"
---
# <a name="iactivescriptprofilercontrol2-interface"></a>Interfejs IActiveScriptProfilerControl2
Zawiera metody, które umożliwią uruchamianie lub zatrzymywanie profilowania, gdy uruchomiony jest skrypt.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|Powiadamia program profilujący do profilowania na wszystkich odpowiednich aparatów obsługi skryptów. Dzięki temu można uzyskać pełny stos wywołań, jeśli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] działa w przypadku uruchamiania profilowania.|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|Powiadamia program profilujący zamierza zatrzymanie profilowania w wszystkich odpowiednich aparatów obsługi skryptów. Dzięki temu można uzyskać pełny stos wywołań, jeśli [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] działa po zatrzymaniu profilowania.|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptProfilerControl Interface](../../winscript/reference/iactivescriptprofilercontrol-interface.md)   
 [Interfejsy profilera aktywnego skryptu](../../winscript/reference/active-script-profiler-interfaces.md)