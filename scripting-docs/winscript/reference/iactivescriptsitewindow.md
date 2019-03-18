---
title: IActiveScriptSiteWindow | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteWindow interface
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3691a874121c00dcccc69958eb5746a2c1d78122
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58149461"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Ten interfejs jest implementowany przez hosty, które obsługują interfejs użytkownika na ten sam obiekt jako [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) . Hosty, które nie obsługują interfejs użytkownika, takich jak serwery, nie będzie implementować `IActiveScriptSiteWindow` interfejsu. Aparat skryptów uzyskuje dostęp do tego interfejsu, wywołując `QueryInterface` z `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Pobiera uchwyt okna, które mogą pełnić rolę właściciela okna podręcznego, który musi być wyświetlana przez silnik wykonywania skryptów.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Powoduje, że host włączyć lub wyłączyć wyświetleniem głównego okna, a także Niemodalne okna dialogowe.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)