---
title: Interfejs IDebugSessionProvider | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: fe73901d92cb42675ff9ec981bd9b90dcca5d546
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58148990"
---
# <a name="idebugsessionprovider-interface"></a>Interfejs IDebugSessionProvider
Podstawowy interfejs dostarczony przez debuger środowiska IDE, aby włączyć hosta i język zainicjować debugowania. Definiuje on sesji debugowania dla działającej aplikacji. Ten interfejs jest implementowany przez Menedżer debugowania maszyny.  
  
 Oprócz metod odziedziczone `IUnknown`, `IDebugSessionProvider` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Inicjuje sesję debugowania przy użyciu określonej aplikacji.|