---
title: Funkcja CvWriteAlert | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvWriteAlertVA
- cvmarkers/CvWriteAlertVW
- cvmarkers/CvWriteAlertA
- cvmarkers/CvWriteAlertW
helpviewer_keywords:
- CvWriteAlertVW method
- CvWriteAlertA method
- CvWriteAlertVA method
- CvWriteAlertW method
ms.assetid: 937aa9d6-278a-4df3-bef7-151441df16d5
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f5c428b471c576c1ca15b73a1c8b2ccfa2cc7b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551224"
---
# <a name="cvwritealert-function"></a>CvWriteAlert — Funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zapisuje alert do pliku śledzenia Concurrency Visualizer.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CvWriteAlertW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteAlertVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### <a name="parameters"></a>Parametry  
 `argList`  
 Lista argumentów.  
  
 `pMarkerSeries`  
 Prawidłowy kontekst serii znaczników. Nie może mieć wartości NULL.  
  
 `pMessage`  
 Ciąg formatu komunikatu. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, gdy komunikat został pomyślnie zapisany. Kod błędu w przypadku wystąpienia błędów. Aby sprawdzić warunek błędu, użyj makr zakończonych powodzeniem i zakończonych niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkers. h  
  
 **Unicode:** CvWriteAlertW, CvWriteAlertVW  
  
 **ANSI:** CvWriteAlertA, CvWriteAlertVA  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja biblioteki C++](../profiling/cpp-library-reference.md)
