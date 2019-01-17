---
title: Interfejs IActiveScriptErrorDebug | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug interface
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d773724d23c61aa72b8cd48917f2cd0bef4a7cb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345204"
---
# <a name="iactivescripterrordebug-interface"></a>Interfejs IActiveScriptErrorDebug
Udostępnia informacje o kontekście dokumentu, błędy kompilacji i wyjątków w czasie wykonywania. `IActiveScriptError::QueryInterface` Obsługuje metody `IActiveScriptErrorDebug` interfejsu.  
  
 Oprócz metod odziedziczone `IActiveScriptError`, `IActiveScriptErrorDebug` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|Tworzy kontekst dokumentu dla tego błędu.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|Udostępnia ramki stosu, który jest wynikiem błędy czasu wykonania.|