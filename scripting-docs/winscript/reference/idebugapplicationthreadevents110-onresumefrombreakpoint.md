---
title: IDebugApplicationThreadEvents110::OnResumeFromBreakPoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110::OnResumeFromBreakPoint
ms.assetid: 4c97b9a3-fced-487e-a81c-e3f8f2cb7927
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 61cb434c5d3514c63446792029b54e2f1413e006
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440477"
---
# <a name="idebugapplicationthreadevents110onresumefrombreakpoint"></a>IDebugApplicationThreadEvents110::OnResumeFromBreakPoint
Wątek jest wznawiana po punkcie przerwania i zostanie uaktywniona jeszcze raz.  
  
> [!IMPORTANT]
> [Interfejs IDebugApplicationThreadEvents110](../../winscript/reference/idebugapplicationthreadevents110-interface.md) jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT OnResumeFromBreakPoint( void );  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie ma parametrów.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugApplicationThreadEvents110, interfejs](../../winscript/reference/idebugapplicationthreadevents110-interface.md)