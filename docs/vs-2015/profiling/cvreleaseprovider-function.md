---
title: Funkcja Cvreleaseprovider — | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d5e611c2a964fcbb78a387a09989436e672ecd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551237"
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider — Funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dostawca znaczników wydań. Zwolnienie dostawcy znaczników nie będzie miało wpływu na wcześniej utworzoną serię znaczników tego dostawcy. Seria znaczników musi być wykorzystana oddzielnie przez wywołanie CvReleaseMarkerSeries —. Niepowodzenie zwolnienia dostawcy powoduje przeciek pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProvider`  
 Kontekst dostawcy. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, gdy dostawca został pomyślnie wydzierżawiony lub kod błędu w przypadku wystąpienia błędów. Aby sprawdzić warunek błędu, użyj makr zakończonych powodzeniem i zakończonych niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkers. h  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja biblioteki C++](../profiling/cpp-library-reference.md)
