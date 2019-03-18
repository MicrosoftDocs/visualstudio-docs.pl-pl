---
title: Interfejs IActiveScriptDebug | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptDebug interface
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6341b5c3763d6e4c836b3bdc0539552fcbe7f980
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58151027"
---
# <a name="iactivescriptdebug-interface"></a>Interfejs IActiveScriptDebug
Implementowany przez aparatów skryptów, w tym obsługę debugowania. Zazwyczaj obiekt, który implementuje `IActiveScriptDebug` również interfejs implementuje `IActiveScript` interfejsu. Jeśli jest to możliwe, należy wywołać `IActiveScript::QueryInterface` metodę, aby uzyskać `IActiveScriptDebug` interfejsu.  
  
 `IActiveScriptDebug` Interfejs udostępnia środki do:  
  
- Inteligentne hosty do zarządzania dokumentami.  
  
- Menedżer debugowania procesów do synchronizowania debugowanie wielu aparatów skryptów.  
  
  Oprócz metod odziedziczone `IUnknown`, `IActiveScriptDebug` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|Zwraca atrybuty tekstu dla dowolnego bloku tekst skryptu.|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|Zwraca atrybuty tekstu dla dowolnego scriptlet.|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|Deleguje do `IDebugDocumentContext::EnumCodeContexts`.|