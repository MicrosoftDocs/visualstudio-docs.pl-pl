---
title: 'marker_series:: write_flag Metoda | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersojb/Concurrency::diagnostic::marker_series::write_flag
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_flag method
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b44c7cf2d2eb0f538b3819265298f1ca4166e6be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200747"
---
# <a name="marker_serieswrite_flag-method"></a>marker_series::write_flag — Metoda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zapisuje flagę w pliku śledzenia Concurrency Visualizer.  
  
## <a name="syntax"></a>Składnia  
  
```  
void write_flag(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `_Format`  
 Ciąg formatu złożonego, który zawiera tekst, który jest przemieszany z zerem lub więcej elementów formatu, który odpowiada obiektom na liście argumentów.  
  
 `_Importance`  
 Poziom ważności.  
  
 `_Category`  
 Kategorii.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkersobj. h  
  
 **Przestrzeń nazw:** Współbieżność::d przesła  
  
## <a name="see-also"></a>Zobacz też  
 [marker_series — Klasa](../profiling/marker-series-class.md)
