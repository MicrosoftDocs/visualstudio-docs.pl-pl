---
title: IActiveScriptWinRTErrorDebug Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 60fbe5efe55b5347eb54eb4d6c010b6ab5903905
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58144241"
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