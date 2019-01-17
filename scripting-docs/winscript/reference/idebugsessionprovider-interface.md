---
title: Interfejs IDebugSessionProvider | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSessionProvider interface
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6d17546d5461a1ad76b144bf2652672ab4aa675
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345152"
---
# <a name="idebugsessionprovider-interface"></a>Interfejs IDebugSessionProvider
Podstawowy interfejs dostarczony przez debuger środowiska IDE, aby włączyć hosta i język zainicjować debugowania. Definiuje on sesji debugowania dla działającej aplikacji. Ten interfejs jest implementowany przez Menedżer debugowania maszyny.  
  
 Oprócz metod odziedziczone `IUnknown`, `IDebugSessionProvider` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Inicjuje sesję debugowania przy użyciu określonej aplikacji.|