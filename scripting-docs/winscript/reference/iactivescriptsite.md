---
title: IActiveScriptSite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67e16e2825f03c9ae452e639d6a086bee584ac95
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58152645"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Implementowany przez hosta, aby utworzyć lokację dla aparatu skryptów Windows. Zazwyczaj ta lokacja będzie skojarzony z kontenerem wszystkie obiekty, które są widoczne dla skryptu (na przykład formantów ActiveX). Zazwyczaj ten kontener będzie odpowiadać dokumentu lub wyświetlanej stronie. Microsoft Internet Explorer, na przykład utworzyć kontener dla każdej strony HTML, które są wyświetlane. Każdy ActiveX kontrolki (lub innego obiektu automatyzacji) na stronie, a silnik wykonywania skryptów, byłoby wyliczalny należących do tego kontenera.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|||  
|-|-|  
|Metoda|Opis|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Pobiera identyfikator ustawień regionalnych używany przez hosta do wyświetlania elementów interfejsu użytkownika.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Uzyskuje informacje na temat elementu, który został dodany do silnika za pomocą wywołania [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) metody.|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Pobiera ciąg zdefiniowany przez hosta, który unikatowo identyfikuje bieżącą wersję dokumentu z punktu widzenia hosta.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Wywołuje się po zakończeniu wykonywania skryptu.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Informuje hosta, że aparat skryptów zmienił Stany.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Informuje hosta, że wystąpił błąd wykonania, gdy aparat był uruchomiony skrypt.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Informuje hosta, że aparat skryptów rozpoczął wykonywanie kodu skryptu.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Informuje hosta, że wykonywanie kodu skryptu zwróciło silnik wykonywania skryptów.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)