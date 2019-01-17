---
title: IProcessDebugManager Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 5feb67b1a616eeaa855b27cb12ea9b3146545ebd
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345126"
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