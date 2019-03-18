---
title: IDebugStackFrameSniffer Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e753261098133eb97f5010dcef5f602d283aac4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58149487"
---
# <a name="idebugstackframesniffer-interface"></a>Interfejs IDebugStackFrameSniffer
Umożliwia wyliczenie ramek stosu logiczne, znane przez składnik. Aparaty skryptów zwykle implementują ten interfejs. Proces debugowania manager wykorzystuje to interfejs, aby znaleźć wszystkie ramki stosu skojarzone z danym wątku.  
  
> [!NOTE]
>  Debuger wywołuje ten interfejs z wewnątrz wątku zainteresowania. Aparat skryptów należy zidentyfikować bieżącego wątku i zwraca moduł wyliczający odpowiednie.  
  
## <a name="methods"></a>Metody  
 Oprócz metod odziedziczone `IUnknown`, `IDebugStackFrameSniffer` interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Zwraca moduł wyliczający ramek stosu dla bieżącego wątku.|