---
title: Metoda IActiveScriptTraceInfo::StartScriptTracing | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6462597f55b6b0ceee885d207572e9669a350600
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093646"
---
# <a name="iactivescripttraceinfostartscripttracing-method"></a>Metoda IActiveScriptTraceInfo::StartScriptTracing
Uruchamia skrypt śledzenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT StartScriptTracing(     [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,     [in] GUID guidContextID );   
```  
  
#### <a name="parameters"></a>Parametry  
 `pSiteTraceInfo`  
 Wskaźnik do IActiveScriptSiteTraceInfo hosta.  
  
 `guidContextId`  
 Identyfikator GUID w kontekście.  
  
## <a name="return-value"></a>Wartość zwracana  
 Możliwe wartości zwracane dla tej metody są następujące:  
  
1.  S_OK: Powodzenie.  
  
2.  E_POINTER: `pSiteTraceInfo` jest wskaźnikiem typu NULL.  
  
3.  E_NOTIMPL: Nie zaimplementowano.