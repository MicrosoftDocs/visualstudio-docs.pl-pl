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
ms.openlocfilehash: 56b2a749eb3553044bda5816639498a0682e37e0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570089"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Zaimplementowane przez hosta w celu utworzenia lokacji dla aparatu skryptów systemu Windows. Zwykle ta lokacja zostanie skojarzona z kontenerem wszystkich obiektów, które są widoczne dla skryptu (na przykład kontrolki ActiveX). Zazwyczaj ten kontener będzie odpowiadać przeglądanemu dokumentowi lub stronie. Na przykład program Microsoft Internet Explorer utworzy taki kontener dla każdej wyświetlanej strony HTML. Każdy formant ActiveX (lub inny obiekt automatyzacji) na stronie i sam aparat skryptów zostałyby wyliczalne w tym kontenerze.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|||  
|-|-|  
|Metoda|Opis|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Pobiera identyfikator ustawień regionalnych, który jest wykorzystywany przez hosta do wyświetlania elementów interfejsu użytkownika.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Uzyskuje informacje o elemencie, który został dodany do aparatu przez wywołanie metody [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Pobiera ciąg zdefiniowany przez hosta, który jednoznacznie identyfikuje bieżącą wersję dokumentu z punktu widzenia hosta.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Wywoływana, gdy skrypt zakończył wykonywanie.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Informuje hosta o zmianie stanu aparatu skryptów.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Informuje hosta, że wystąpił błąd wykonywania, gdy aparat uruchomił skrypt.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Informuje hosta o tym, że aparat obsługi skryptów rozpoczął wykonywanie kodu skryptu.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Informuje hosta, że aparat obsługi skryptów zwrócił kod skryptu wykonywania.|  
  
## <a name="see-also"></a>Zobacz także  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)