---
title: Interfejs IActiveScriptStats | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptStats interface
ms.assetid: dbe84d6f-1b77-4877-aced-cd4e01ead5b5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7a0e1e616fdee2dac58c8a5a1d24ed120b28bc2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991976"
---
# <a name="iactivescriptstats-interface"></a>Interfejs IActiveScriptStats
Umożliwia hosta do wykonywania zapytań statystyki uruchamianie skryptu. Hosta można użyć tych informacji, aby określić, jeśli skrypt zajęło zbyt długo.  
  
 Oprócz metod odziedziczone `IUnknown`, `IActiveScriptStats` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)|Zwraca jedną z statystyki skrypt standardowy.|  
|[IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)|Zwraca statystyki skryptu niestandardowego.|  
|[IActiveScriptStats::ResetStats](../../winscript/reference/iactivescriptstats-resetstats.md)|Resetuje statystyki dla tego skryptu.|