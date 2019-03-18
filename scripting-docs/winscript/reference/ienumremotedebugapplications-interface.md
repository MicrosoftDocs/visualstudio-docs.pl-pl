---
title: Interfejs IEnumRemoteDebugApplications | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IEnumRemoteDebugApplications interface
ms.assetid: ceb5fbe7-d131-4352-9dd1-af80acd3f3f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 430551002bc7603d86f9c7fb624ec438734bd766
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58150624"
---
# <a name="ienumremotedebugapplications-interface"></a>Interfejs IEnumRemoteDebugApplications
Wyliczenie obiektów aplikacji. Ten interfejs może służyć do wyliczenia uruchomionych aplikacji na komputerze dla okna dialogowego "Dołączanie do aplikacji".  
  
 Oprócz metod odziedziczone `IUnknown`, `IEnumRemoteDebugApplications` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IEnumRemoteDebugApplications::Clone](../../winscript/reference/ienumremotedebugapplications-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan jako bieżący modułu wyliczającego.|  
|[IEnumRemoteDebugApplications::Next](../../winscript/reference/ienumremotedebugapplications-next.md)|Pobiera określoną liczbę segmentów w kolejności wyliczenia.|  
|[IEnumRemoteDebugApplications::Reset](../../winscript/reference/ienumremotedebugapplications-reset.md)|Resetuje sekwencji wyliczenia na początku.|  
|[IEnumRemoteDebugApplications::Skip](../../winscript/reference/ienumremotedebugapplications-skip.md)|Pomija określoną liczbę segmentów w kolejności wyliczenia.|