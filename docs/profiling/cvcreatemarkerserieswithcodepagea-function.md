---
title: Cvcreatemarkerserieswithcodepagea — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 63fe3de8c4322e378f110813ac93fa523f3453ba
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750379"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>Cvcreatemarkerserieswithcodepagea — funkcja
Tworzy serię znacznika dla danego dostawcy oraz określonej strony kodowej. Ta funkcja umożliwia określanie strony kodowej jawnie dla tekstu zapisywane przez funkcje interfejsu API ANSI znacznika. Ustawianie strony kodowej mogą być przydatne w przypadku, gdy śledzenie jest przechwycony i następnie przeanalizowane na kilka różnych maszyn z różnych ustawień regionalnych/języków. Domyślnie używany jest zwracane przez funkcję GetACP() stronę kodową.  
  
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
 Obiekt dostawcy poprzednio inicjowany przez CvInitProvider. Nie może mieć wartości NULL.  
  
 `pSeriesName`  
 Nazwa serii znacznika. Nie może mieć wartości NULL, ale może być ciągiem pustym.  
  
 `nTextCodePage`  
 Strona prawidłowy kod.  
  
 `ppMarkerSeries`  
 Adres zmiennej danych wyjściowych, która zapisze w kontekście serii znacznika. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK serii znacznika został utworzony pomyślnie lub kod błędu w przypadku zostały wszystkie błędy. Użyj makra powiodło się/nie powiodło się, aby sprawdzić warunku błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** *cvmarkers.h*  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do biblioteki C++](../profiling/cpp-library-reference.md)