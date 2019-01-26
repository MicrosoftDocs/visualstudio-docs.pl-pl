---
title: CvCreateMarkerSeriesWithCodePageA Function | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 410e23163d2d12ac141aecdc7d7f65036ff26406
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942077"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA function
Tworzy serię znacznika dla danego dostawcy oraz określonej strony kodowej. Ta funkcja może służyć do określenia strony kodowej jawnie dla tekstu, napisanych przez funkcje API ANSI znacznika. Ustawianie strony kodowej może być przydatne w przypadku, gdy śledzenie jest przechwycony i następnie analizowane na różnych maszynach, za pomocą różnych ustawień regionalnych/języków. Domyślnie używany jest zwrócona przez funkcję GetACP() strony kodowej.  
  
## <a name="syntax"></a>Składnia  
  
```C  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProvider`  
 Poprzednio inicjowany przez cvinitprovider — obiekt dostawcy. Nie może mieć wartości NULL.  
  
 `pSeriesName`  
 Nazwa serii znacznika. Nie może mieć wartości NULL, ale dozwolone jest pustym ciągiem.  
  
 `nTextCodePage`  
 Prawidłowy kod strony.  
  
 `ppMarkerSeries`  
 Adres zmiennej danych wyjściowych, który będzie przechowywał znaczników serii kontekstu. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK znaczników serii został pomyślnie utworzony lub kod błędu w przypadku zostały wszystkie błędy. Aby sprawdzić, czy warunek błędu, należy użyć makra Powodzenie/niepowodzenie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** *cvmarkers.h*  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)