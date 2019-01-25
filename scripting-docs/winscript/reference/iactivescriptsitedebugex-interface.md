---
title: IActiveScriptSiteDebugEx Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e390b610d6912de0078b817c9dfb503e5924a374
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54797433"
---
# <a name="iactivescriptsitedebugex-interface"></a>Interfejs IActiveScriptSiteDebugEx

Implementuje ten interfejs, wraz z `IActiveScriptSiteDebug` interfejsu, jeśli piszesz hosta, który musi odbieraj powiadomienie o błędów czasu wykonywania w aplikacji i opcjonalnie dołączyć do aplikacji do debugowania. Menedżer debugowania procesów zapewnia powiadomienie za pośrednictwem `IActiveScriptDebug` Jeśli Just-In-Time debugera skryptów znajduje się na komputerze. Nie Just-In-Time debugera skryptów czy znaleziono, menedżerów PDM zapewnia powiadomienie za pośrednictwem `IActiveScriptDebugEx` zamiast tego.

Aby uzyskać powiadomienie z informacją o błędów czasu wykonywania, hosta musi obsługiwać `ActiveScriptSiteDebug::OnScriptErrorDebug`. Oparte na akcję użytkownika, następnie można zdecydować, czy dołączyć debuger wewnętrzny i wrócić, czy zwracać uruchamiania w debugerze programu OnScriptErrorDebug `pfEnterDebugger` parametru.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności

|Metoda|Opis|
|------------|-----------------|
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Informuje, że host o błąd czasu wykonywania skryptu po procesie debugowanie Menedżera nie zewnętrznego debugera Just In Time.|