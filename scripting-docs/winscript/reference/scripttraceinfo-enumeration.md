---
title: Wyliczenie SCRIPTTRACEINFO | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ed2c6566db8209280be7f102a55c7de8cf85c44
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58155813"
---
# <a name="scripttraceinfo-enumeration"></a>Wyliczenie SCRIPTTRACEINFO
Reprezentuje zdarzenie skryptu, które jest śledzone. Używane w [metoda IActiveScriptSiteTraceInfo::SendScriptTraceInfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef enum tagSCRIPTTRACEINFO {      SCRIPTTRACEINFO_SCRIPTSTART = 0,      SCRIPTTRACEINFO_SCRIPTEND   = 1,      SCRIPTTRACEINFO_COMCALLSTART    = 2,      SCRIPTTRACEINFO_COMCALLEND  = 3,      SCRIPTTRACEINFO_CREATEOBJSTART  = 4,      SCRIPTTRACEINFO_CREATEOBJEND    = 5,      SCRIPTTRACEINFO_GETOBJSTART = 6,      SCRIPTTRACEINFO_GETOBJEND   = 7,  } SCRIPTTRACEINFO ;  
```  
  
## <a name="enumeration-values"></a>Wartości wyliczenia  
  
|||  
|-|-|  
|SCRIPTTRACEINFO_SCRIPTSTART|Uruchomienie skryptu.|  
|SCRIPTTRACEINFO_SCRIPTEND|Koniec skryptu.|  
|SCRIPTTRACEINFO_COMCALLSTART|Początek wywołania modelu COM.|  
|SCRIPTTRACEINFO_COMCALLEND|Koniec wywołania modelu COM.|  
|SCRIPTTRACEINFO_CREATEOBJSTART|Rozpoczęcie tworzenia obiektów.|  
|SCRIPTTRACEINFO_CREATEOBJEND|Data zakończenia tworzenia obiektu.|  
|SCRIPTTRACEINFO_GETOBJSTART|Początek wywołania GetObject.|  
|SCRIPTTRACEINFO_GETOBJEND|Koniec wywołania GetObject.|