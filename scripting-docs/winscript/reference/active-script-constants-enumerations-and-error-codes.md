---
title: Aktywnego skryptu stałe, wyliczenia i kody błędów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f5e25070aa92a9464bfc92433c0d2b7763232fb6
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347622"
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>Kody błędów, stałe i wyliczenia aktywnego skryptu
W tej sekcji opisano, wyliczenia i kodów błędów występujących podczas aparatów obsługi skryptów Windows.  
  
## <a name="constants"></a>Stałe  
  
|Stała|Opis|  
|--------------|-----------------|  
|[SCRIPTTHREADID, stałe](../../winscript/reference/scriptthreadid-constants.md)|Określa typ wątku.|  
  
## <a name="properties"></a>Właściwości  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[SCRIPTPROP_HOSTKEEPALIVE, właściwość](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Służy do określania, czy aparat skryptów powinny być przechowywane w pełni funkcjonalne, w przypadku innych odwołań.|  
  
## <a name="enumerations"></a>Wyliczenia  
  
|Wyliczenie|Opis|  
|-----------------|-----------------|  
|[SCRIPTGCTYPE, wyliczenie](../../winscript/reference/scriptgctype-enumeration.md)|Typ wyrzucania elementów bezużytecznych do wykonania.|  
|[SCRIPTLANGUAGEVERSION, wyliczenie](../../winscript/reference/scriptlanguageversion-enumeration.md)|Określa możliwości skryptów wersji.|  
|[SCRIPTSTATE, wyliczenie](../../winscript/reference/scriptstate-enumeration.md)|Określa stan silnika wykonywania skryptów.|  
|||  
|[SCRIPTTHREADSTATE, wyliczenie](../../winscript/reference/scriptthreadstate-enumeration.md)|Określa stan wątku w silnik wykonywania skryptów.|  
|[SCRIPTTRACEINFO, wyliczenie](../../winscript/reference/scripttraceinfo-enumeration.md)|Reprezentuje zdarzenie skryptu, które jest śledzone. Używane w [metoda IActiveScriptSiteTraceInfo::SendScriptTraceInfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[SCRIPTUICHANDLING, wyliczenie](../../winscript/reference/scriptuichandling-enumeration.md)|Przedstawia sposób obsługi kontrolki interfejsu użytkownika.|  
|[SCRIPTUICITEM, wyliczenie](../../winscript/reference/scriptuicitem-enumeration.md)|Reprezentuje typ elementu interfejsu użytkownika. Używane w [metoda IActiveScriptSiteUIControl::GetUIBehavior](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## <a name="error-codes"></a>Kody błędów  
  
|Kod błędu|Opis|  
|----------------|-----------------|  
|[SCRIPT_E_PROPAGATE, kod błędu](../../winscript/reference/script-e-propagate-error-code.md)|Błąd skryptu jest są propagowane do obiektu wywołującego, która może być w innym wątku.|  
|[SCRIPT_E_RECORDED, kod błędu](../../winscript/reference/script-e-recorded-error-code.md)|Błąd został przekazany między aparatu skryptów i hostem.|  
|[SCRIPT_E_REPORTED, kod błędu](../../winscript/reference/script-e-reported-error-code.md)|Aparat skryptów zgłosił nieobsługiwany wyjątek do hosta.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)