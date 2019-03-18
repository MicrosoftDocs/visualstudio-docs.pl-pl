---
title: Interfejs IDebugStackFrameSnifferEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSnifferEx interface
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc6e892c00a2d86e784857f08772550897e1ec4e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58157189"
---
# <a name="idebugstackframesnifferex-interface"></a>Interfejs IDebugStackFrameSnifferEx
Umożliwia wyliczenie ramek stosu logiczne, znane przez składnik. Aparaty skryptów zwykle implementują ten interfejs. Proces debugowania manager wykorzystuje to interfejs, aby znaleźć wszystkie ramki stosu skojarzone z danym wątku.  
  
> [!NOTE]
>  Ten interfejs jest wywoływana z wewnątrz wątku zainteresowania. Implementacja interfejsu należy zidentyfikować bieżącego wątku i zwraca moduł wyliczający odpowiednie.  
  
 Oprócz metod odziedziczone `IDebugStackFrameSniffer`, `IDebugStackFrameSnifferEx` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Zwraca moduł wyliczający ramek stosu dla bieżącego wątku.|