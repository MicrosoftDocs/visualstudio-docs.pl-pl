---
title: ResumeTracking | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- ResumeTracking
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 75c1a94e9db6e1a141668f6ba314c39cedc3fd6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159219"
---
# <a name="resumetracking"></a>ResumeTracking
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wznawia śledzenie w bieżącym kontekście.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) z [powodzenie] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->), jeśli śledzenie zostało wznowione. [E_FAIL] (<!-- TODO: review code entity reference <xref:assetId:///E_FAIL?qualifyHint=False&amp;autoUpgrade=True>  -->) jest zwracany, jeśli nie można wznowić śledzenia, ponieważ kontekst nie jest dostępny.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** FileTracker. h  
  
## <a name="see-also"></a>Zobacz też  
 [SuspendTracking](../msbuild/suspendtracking.md)
