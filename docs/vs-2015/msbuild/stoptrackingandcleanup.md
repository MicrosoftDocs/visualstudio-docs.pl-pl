---
title: StopTrackingAndCleanup | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- StopTrackingAndCleanup
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7b4a6cca4010284c9a75767710710d28c093c271
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203112"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Powoduje zatrzymanie śledzenia i zwolnienie dowolnej pamięci używanej przez sesję śledzenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) z [powodzenie] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) Ustaw bit, jeśli śledzenie zostało zatrzymane.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** FileTracker. h  
  
## <a name="see-also"></a>Zobacz też  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
