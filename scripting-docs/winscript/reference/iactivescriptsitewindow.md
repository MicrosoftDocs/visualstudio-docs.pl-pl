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
ms.openlocfilehash: 1ee680a3d00c6736549b03ce8fee5593a7a8c5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575896"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Ten interfejs jest implementowany przez hosty obsługujące interfejs użytkownika w tym samym obiekcie co [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) . Hosty, które nie obsługują interfejsu użytkownika, takie jak serwery, nie implementują interfejsu `IActiveScriptSiteWindow`. Aparat skryptów uzyskuje dostęp do tego interfejsu, wywołując `QueryInterface` z `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Pobiera uchwyt okna, który może działać jako właściciel okna podręcznego, który musi być wyświetlany przez aparat skryptów.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Powoduje włączenie lub wyłączenie okna głównego oraz niemodalnych okien dialogowych.|  
  
## <a name="see-also"></a>Zobacz także  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)