---
title: IDebugStackFrame Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrame interface
ms.assetid: e95c1b4f-17c1-490c-a56b-c25fa45d4822
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8f645d6460ff15734348267b5138b1b6edea071
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58149552"
---
# <a name="idebugstackframe-interface"></a>Interfejs IDebugStackFrame
Reprezentuje ramkę stosu logicznych na stosie wątku. Wywołaj `IDebugStackFrame::QueryInterface` metodę, aby uzyskać `IDebugExpressionContext` interfejs, który umożliwia wyrażenie oceny i obejrzyj systemu windows.  
  
 Oprócz metod odziedziczone `IUnknown`, `IDebugStackFrame` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugStackFrame::GetCodeContext](../../winscript/reference/idebugstackframe-getcodecontext.md)|Zwraca bieżący kontekst kodu skojarzone z ramki stosu.|  
|[IDebugStackFrame::GetDescriptionString](../../winscript/reference/idebugstackframe-getdescriptionstring.md)|Zwraca opis krótki lub długo tekstowych ramki stosu.|  
|[IDebugStackFrame::GetLanguageString](../../winscript/reference/idebugstackframe-getlanguagestring.md)|Zwraca krótki lub długo tekstowe Opis języka.|  
|[IDebugStackFrame::GetThread](../../winscript/reference/idebugstackframe-getthread.md)|Zwraca wątek skojarzony z tą ramką stosu.|  
|[IDebugStackFrame::GetDebugProperty](../../winscript/reference/idebugstackframe-getdebugproperty.md)|Zwraca przeglądarkę właściwości dla bieżącej ramki.|