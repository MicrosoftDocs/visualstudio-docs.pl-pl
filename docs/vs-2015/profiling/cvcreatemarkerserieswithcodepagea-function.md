---
title: Funkcja Cvcreatemarkerserieswithcodepagea — | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 635a872372ab775eceb00854a616884f3fc19fef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155531"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA — Funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tworzy serię znaczników dla danego dostawcy i określonej strony kodowej. Ta funkcja może służyć do określania strony kodowej jawnie dla tekstu pisanego przez funkcje ANSI interfejsu API znaczników. Ustawienie strony kodowej może być przydatne w przypadku, gdy śledzenie jest przechwytywane, a następnie analizowane na różnych maszynach przy użyciu różnych ustawień regionalnych/języków. Domyślnie jest używana strona kodowa zwrócona przez funkcję GetACP ().  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProvider`  
 Obiekt dostawcy został wcześniej zainicjowany przez CvInitProvider —. Nie może mieć wartości NULL.  
  
 `pSeriesName`  
 Nazwa serii znaczników. Nie może mieć wartości NULL, ale jest dozwolony pusty ciąg.  
  
 `nTextCodePage`  
 Prawidłowa strona kodowa.  
  
 `ppMarkerSeries`  
 Adres zmiennej wyjściowej, w której będzie przechowywany kontekst serii znaczników. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, gdy seria znaczników zostanie pomyślnie utworzona lub kod błędu w przypadku wystąpienia błędów. Aby sprawdzić warunek błędu, użyj makr zakończonych powodzeniem i zakończonych niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkers. h  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja biblioteki C++](../profiling/cpp-library-reference.md)
