---
title: 'marker_series:: write_alert Metoda | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert
helpviewer_keywords:
- Concurrency::diagnostic:marker_series::write_alert method
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d65bec449938a55ee9a415dd86db1ba07efbdb1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200760"
---
# <a name="marker_serieswrite_alert-method"></a>marker_series::write_alert — Metoda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zapisuje alert do pliku śledzenia Concurrency Visualizer.  
  
## <a name="syntax"></a>Składnia  
  
```  
void write_alert(  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `_Format`  
 Ciąg formatu złożonego, który zawiera tekst, który jest przemieszany z zerem lub więcej elementów formatu, który odpowiada obiektom na liście argumentów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkersobj. h  
  
 **Przestrzeń nazw:** Współbieżność::d przesła  
  
## <a name="see-also"></a>Zobacz też  
 [marker_series — Klasa](../profiling/marker-series-class.md)
