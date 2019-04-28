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
ms.openlocfilehash: 5c9181b5013a9584a2a686ed0e499698be0b62b9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432257"
---
# <a name="idebugstackframesniffer-interface"></a>Interfejs IDebugStackFrameSniffer
Umożliwia wyliczenie ramek stosu logiczne, znane przez składnik. Aparaty skryptów zwykle implementują ten interfejs. Proces debugowania manager wykorzystuje to interfejs, aby znaleźć wszystkie ramki stosu skojarzone z danym wątku.  
  
> [!NOTE]
> Debuger wywołuje ten interfejs z wewnątrz wątku zainteresowania. Aparat skryptów należy zidentyfikować bieżącego wątku i zwraca moduł wyliczający odpowiednie.  
  
## <a name="methods"></a>Metody  
 Oprócz metod odziedziczone `IUnknown`, `IDebugStackFrameSniffer` interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Zwraca moduł wyliczający ramek stosu dla bieżącego wątku.|