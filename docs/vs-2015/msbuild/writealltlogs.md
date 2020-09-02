---
title: WriteAllTLogs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- WriteAllTLogs
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 371357249bb9674a636859c995ad076eb41c2a08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192590"
---
# <a name="writealltlogs"></a>WriteAllTLogs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zapisuje dzienniki śledzenia dla wszystkich wątków i kontekstów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### <a name="parameters"></a>Parametry  
 podczas `intermediateDirectory`  
 Katalog, w którym ma być przechowywany dziennik śledzenia.  
  
 podczas `tlogRootName`  
 Nazwa głównego pliku dziennika.  
  
## <a name="return-value"></a>Wartość zwracana  
 [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) z [powodzenie] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) Ustaw bit w przypadku utworzenia kontekstu śledzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** FileTracker. h  
  
## <a name="see-also"></a>Zobacz też  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)
