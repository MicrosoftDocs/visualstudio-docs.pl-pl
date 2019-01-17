---
title: Interfejs ISetNextStatement | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ac2d6dd0da14be5a624cff0b55985770b8d70fdf
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344060"
---
# <a name="isetnextstatement-interface"></a>Interfejs ISetNextStatement
Ten interfejs jest implementowany przez tłumacza, aby umożliwić Menedżer debugowania procesów do zaktualizowania bieżącej instrukcji. Jest implementowany z obiekt w ramce stosu i menedżerów PDM uzyskuje ten interfejs, za pomocą funkcji QueryInterface.  
  
 interfejs zapewnia metody, które są przydatne do ustawiania punkt wykonania, która określa następną instrukcję do wykonania.  
  
 Oprócz metod odziedziczone `IUnknown`, `ISetNextStatement` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Określa, czy można ustawić punkt wykonania do określonej lokalizacji.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Ustawia punkt wykonania do określonej lokalizacji.|