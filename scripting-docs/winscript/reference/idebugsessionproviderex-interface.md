---
title: Interfejs IDebugSessionProviderEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9bf341adeaeb17c8986b1b30b12f58113aef562
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58146776"
---
# <a name="idebugsessionproviderex-interface"></a>Interfejs IDebugSessionProviderEx
Podstawowy interfejs dostarczony przez debuger środowiska IDE, aby włączyć debugowanie inicjowane przez hosta i języka. Definiuje on sesji debugowania dla działającej aplikacji. Ten interfejs jest implementowany przez Menedżer debugowania komputera.  
  
 Oprócz metod odziedziczone `IUnknown`, `IDebugSessionProviderEx` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Określa, czy debugowanie Just In Time jest możliwe z określoną aplikacją.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Inicjuje sesję debugowania przy użyciu określonej aplikacji.|