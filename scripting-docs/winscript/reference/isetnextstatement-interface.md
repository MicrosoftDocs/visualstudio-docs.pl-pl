---
title: Interfejs ISetNextStatement | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de300a7af8492e6431f6b8513cde84a15895ad96
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58148428"
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