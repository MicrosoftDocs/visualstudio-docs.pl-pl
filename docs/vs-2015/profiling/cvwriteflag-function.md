---
title: Funkcja CvWriteFlag | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvWriteFlagExVA
- cvmarkers/CvWriteFlagExW
- cvmarkers/CvWriteFlagExVW
- cvmarkers/CvWriteFlagExA
helpviewer_keywords:
- CvWriteFlagExW method
- CvWriteFlagExVA method
- CvWriteFlagExA method
- CvWriteFlagExVW method
ms.assetid: ee9da1e2-7b34-4cba-81e2-215d25d32e4d
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bea5e2acea9a89c5a3b2fdfba441530a74ad8515
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177741"
---
# <a name="cvwriteflag-function"></a>CvWriteFlag — Funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zapisuje flagę w pliku śledzenia Concurrency Visualizer.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CvWriteFlagExW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteFlagExA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteFlagExVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteFlagExVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### <a name="parameters"></a>Parametry  
 `argList`  
 Lista argumentów.  
  
 `category`  
 Kategorii.  
  
 `level`  
 Poziom ważności.  
  
 `pMarkerSeries`  
 Prawidłowy kontekst serii znaczników. Nie może mieć wartości NULL.  
  
 `pMessage`  
 Ciąg formatu komunikatu. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, gdy komunikat został pomyślnie zapisany. Kod błędu w przypadku wystąpienia błędów. Aby sprawdzić warunek błędu, użyj makr zakończonych powodzeniem i zakończonych niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkers. h  
  
 **Unicode:** CvWriteFlagExW, CvWriteFlagExVW  
  
 <strong>ANSI:</strong> CvWriteFlagExA, CvWriteFlagExVA  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja biblioteki C++](../profiling/cpp-library-reference.md)
