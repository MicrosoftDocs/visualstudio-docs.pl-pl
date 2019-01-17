---
title: Interfejs IDebugExpression | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugExpression interface
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9684253343aa83cf95f7d816781705eab7fbc327
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345521"
---
# <a name="idebugexpression-interface"></a>Interfejs IDebugExpression
Reprezentuje asynchronicznie obliczane wyrażenie. Aparaty skryptów zwykle implementują ten interfejs. Debuger IDE zazwyczaj używa tego interfejsu do włączenia okna natychmiastowego wykonania lub okno czujki.  
  
> [!NOTE]
>  `IDebugExpression` Interfejs jest dostępny tylko z ramki stosu.  
  
 Oprócz metod odziedziczone `IUnknown`, `IDebugExpression` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Rozpoczyna się obliczania wyrażenia.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Przerywa wyrażenia.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Określa, jeśli operacja została zakończona.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Zwraca wynik obliczania wyrażenia jako ciąg i wartości zwracanej wykonać operację.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Zwraca wynik obliczania wyrażenia jako właściwość debugowania i wartość zwracana wykonać operację.|