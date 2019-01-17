---
title: Interfejs IDebugSessionProviderEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fae1cf673f47d3be586f83320b2d2c38c817e2cf
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349221"
---
# <a name="idebugsessionproviderex-interface"></a>Interfejs IDebugSessionProviderEx
Podstawowy interfejs dostarczony przez debuger środowiska IDE, aby włączyć debugowanie inicjowane przez hosta i języka. Definiuje on sesji debugowania dla działającej aplikacji. Ten interfejs jest implementowany przez Menedżer debugowania komputera.  
  
 Oprócz metod odziedziczone `IUnknown`, `IDebugSessionProviderEx` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Określa, czy debugowanie Just In Time jest możliwe z określoną aplikacją.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Inicjuje sesję debugowania przy użyciu określonej aplikacji.|