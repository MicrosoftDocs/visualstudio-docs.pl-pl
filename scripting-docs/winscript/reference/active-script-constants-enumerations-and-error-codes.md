---
title: Stałe, wyliczenia i kody błędów aktywnego skryptu | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e03bef99c2297d517aa5234db49820a2b9600ce7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572712"
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>Kody błędów, stałe i wyliczenia aktywnego skryptu
W tej sekcji opisano wyliczenia i kody błędów używane w aparatach skryptów systemu Windows.  
  
## <a name="constants"></a>Stałe  
  
|Stała|Opis|  
|--------------|-----------------|  
|[SCRIPTTHREADID, stałe](../../winscript/reference/scriptthreadid-constants.md)|Określa typ wątku.|  
  
## <a name="properties"></a>Właściwości  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[SCRIPTPROP_HOSTKEEPALIVE, właściwość](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Służy do określania, czy aparat skryptów ma być w pełni funkcjonalny, jeśli istnieją zaległe odwołania.|  
  
## <a name="enumerations"></a>Wyliczenia  
  
|Wyliczenie|Opis|  
|-----------------|-----------------|  
|[SCRIPTGCTYPE, wyliczenie](../../winscript/reference/scriptgctype-enumeration.md)|Typ wyrzucania elementów bezużytecznych do wykonania.|  
|[SCRIPTLANGUAGEVERSION, wyliczenie](../../winscript/reference/scriptlanguageversion-enumeration.md)|Określa możliwe wersje skryptów.|  
|[SCRIPTSTATE, wyliczenie](../../winscript/reference/scriptstate-enumeration.md)|Określa stan aparatu obsługi skryptów.|  
|||  
|[SCRIPTTHREADSTATE, wyliczenie](../../winscript/reference/scriptthreadstate-enumeration.md)|Określa stan wątku w aparacie skryptów.|  
|[SCRIPTTRACEINFO, wyliczenie](../../winscript/reference/scripttraceinfo-enumeration.md)|Reprezentuje śledzone zdarzenie skryptu. Używany w [metodzie IActiveScriptSiteTraceInfo:: SendScriptTraceInfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[SCRIPTUICHANDLING, wyliczenie](../../winscript/reference/scriptuichandling-enumeration.md)|Przedstawia sposób, w jaki formant interfejsu użytkownika powinien być obsługiwany.|  
|[SCRIPTUICITEM, wyliczenie](../../winscript/reference/scriptuicitem-enumeration.md)|Reprezentuje typ elementu interfejsu użytkownika. Używany w [metodzie IActiveScriptSiteUIControl:: GetUIBehavior](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## <a name="error-codes"></a>Kody błędów  
  
|Kod błędu|Opis|  
|----------------|-----------------|  
|[SCRIPT_E_PROPAGATE, kod błędu](../../winscript/reference/script-e-propagate-error-code.md)|Błąd skryptu jest propagowany do obiektu wywołującego, który może znajdować się w innym wątku.|  
|[SCRIPT_E_RECORDED, kod błędu](../../winscript/reference/script-e-recorded-error-code.md)|Przekazano błąd między aparatem skryptu i hostem.|  
|[SCRIPT_E_REPORTED, kod błędu](../../winscript/reference/script-e-reported-error-code.md)|Aparat skryptów zgłosił nieobsłużony wyjątek do hosta.|  
  
## <a name="see-also"></a>Zobacz także  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)