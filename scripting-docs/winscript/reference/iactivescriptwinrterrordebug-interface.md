---
title: IActiveScriptWinRTErrorDebug Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug Interface
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2355b9aa38abbed2ca66964a07bb47082eb76c32
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346504"
---
# <a name="iactivescriptwinrterrordebug-interface"></a>Interfejs IActiveScriptWinRTErrorDebug
Implementowany przez aparat języka JavaScript, aby zapewnić rozszerzone informacje o błędzie Windows Runtime z [wyliczenie BREAKREASON](../../winscript/reference/breakreason-enumeration.md) zdarzeń. Możecie QueryInterface można pobrać go z [IActiveScriptError](../../winscript/reference/iactivescripterror.md) obiektu.  
  
> [!IMPORTANT]
>  Interfejs jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="methods"></a>Metody  
 `IActiveScriptWinRTErrorDebug` Interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|Zwraca możliwości identyfikatora SID dla błędu środowiska wykonawczego Windows, jeśli jest dostępny.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|Zwraca środowiska uruchomieniowego Windows ograniczony ciąg odwołania błąd, jeśli jest dostępny.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|Zwraca środowiska uruchomieniowego Windows ograniczony ciąg błędu, jeśli jest dostępny.|