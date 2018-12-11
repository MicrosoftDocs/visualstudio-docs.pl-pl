---
title: Cvcreatedefaultmarkerseriesofdefaultprovider — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c68c7870430033d9ff20b94f51e516038c9eba6
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749190"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>Cvcreatedefaultmarkerseriesofdefaultprovider — funkcja
Tworzy domyślny znacznik serii domyślnego dostawcy.  
  
## <a name="syntax"></a>Składnia  
  
```C  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppProvider`  
 Adres zmiennej obiektu dostawcy. Adres nie może mieć wartości NULL, zmienna może mieć dowolną wartość.  
  
 `ppMarkerSeries`  
 Adres zmiennej obiektu serii znacznika. Adres nie może mieć wartości NULL, zmienna może mieć dowolną wartość.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK podczas serii zarówno dostawcy, jak i znacznika pomyślnie zostały utworzone lub kod błędu w przypadku zostały wszystkie błędy. Użyj makra powiodło się/nie powiodło się, aby sprawdzić warunku błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** *cvmarkers.h*  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do biblioteki C++](../profiling/cpp-library-reference.md)