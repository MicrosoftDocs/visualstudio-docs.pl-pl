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
ms.openlocfilehash: dccd9210908922951c20378868c33b3389cbed4f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432250"
---
# <a name="idebugstackframesnifferex-interface"></a>Interfejs IDebugStackFrameSnifferEx
Umożliwia wyliczenie ramek stosu logiczne, znane przez składnik. Aparaty skryptów zwykle implementują ten interfejs. Proces debugowania manager wykorzystuje to interfejs, aby znaleźć wszystkie ramki stosu skojarzone z danym wątku.  
  
> [!NOTE]
> Ten interfejs jest wywoływana z wewnątrz wątku zainteresowania. Implementacja interfejsu należy zidentyfikować bieżącego wątku i zwraca moduł wyliczający odpowiednie.  
  
 Oprócz metod odziedziczone `IDebugStackFrameSniffer`, `IDebugStackFrameSnifferEx` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Zwraca moduł wyliczający ramek stosu dla bieżącego wątku.|