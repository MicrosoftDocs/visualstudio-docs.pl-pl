---
title: IProcessDebugManager Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProcessDebugManager interface
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d68c044cdc3d523841cc56814b8ca34bcd8aa037
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58157246"
---
# <a name="iprocessdebugmanager-interface"></a>Interfejs IProcessDebugManager
Podstawowy interfejs Menedżer debugowania procesów. Ten interfejs może utworzyć, Dodaj lub Usuń aplikację wirtualną z procesu. Można ją wyliczanie ramek stosu i wątki aplikacji.  
  
 Oprócz metod odziedziczone `IUnknown`, `IProcessDebugManager` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Tworzy nowy obiekt aplikacji debugowania dla tej aplikacji.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Zwraca domyślny obiekt aplikacji dla bieżącego procesu.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Dodaje aplikację do listy maszyny Menedżer debugowania działających aplikacji.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Usuwa aplikację z uruchomionych listy aplikacji.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Tworzy nowy Pomocnik dokumentu debugowania dla tej aplikacji.|