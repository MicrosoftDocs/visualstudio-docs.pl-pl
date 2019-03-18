---
title: IApplicationDebuggerUI Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IApplicationDebuggerUI interface
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f138492e5b0a465bb0f101c15457ed1021ab3d5a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58146187"
---
# <a name="iapplicationdebuggerui-interface"></a>Interfejs IApplicationDebuggerUI
Implementowany przez debugera zintegrowanego środowiska programistycznego (IDE) (oprócz `IApplicationDebugger`) do zapewnienia składnik zewnętrzny więcej kontroli nad interfejsu użytkownika (UI) debugera.  
  
 Oprócz metod odziedziczone `IUnknown`, `IApplicationDebuggerUI` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|Przesuwa okno zawiera dokument określonego debugowania do góry w debugerze interfejsu użytkownika.|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|Wywołuje okno zawierające kontekście danego dokumentu do góry w interfejsie użytkownika debugera i przewija okna do kontekstu.|