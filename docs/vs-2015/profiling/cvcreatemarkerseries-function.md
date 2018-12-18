---
title: Funkcja CvCreateMarkerSeries | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52ef56d1e33ddb66a4c35f7c46596ea080478a6c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734720"
---
# <a name="cvcreatemarkerseries-function"></a>CvCreateMarkerSeries — Funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tworzy serię znacznika dla danego dostawcy.  
  
## <a name="syntax"></a>Składnia  
  
```  
_Check_return_ HRESULT CvCreateMarkerSeriesW(  
    _In_ PCV_PROVIDER  pProvider,  
    _In_ LPCWSTR pSeriesName,  
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);  
  
_Check_return_ HRESULT CvCreateMarkerSeriesA(  
    _In_ PCV_PROVIDER  pProvider,  
    _In_ LPCSTR pSeriesName,  
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProvider`  
 Poprzednio inicjowany przez cvinitprovider — obiekt dostawcy. Nie może mieć wartości NULL.  
  
 `pSeriesName`  
 Nazwa serii znacznika. Nie może mieć wartości NULL, ale dozwolone jest pustym ciągiem.  
  
 `ppMarkerSeries`  
 Adres zmiennej danych wyjściowych, który będzie przechowywał znaczników serii kontekstu. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK znaczników serii został pomyślnie utworzony lub kod błędu w przypadku zostały wszystkie błędy. Aby sprawdzić, czy warunek błędu, należy użyć makra Powodzenie/niepowodzenie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkers.h  
  
 **Unicode:** cvcreatemarkerseriesw —  
  
 **ANSI:** cvcreatemarkerseriesa —  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)



