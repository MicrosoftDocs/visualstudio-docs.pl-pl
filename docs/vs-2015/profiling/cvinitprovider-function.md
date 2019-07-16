---
title: Funkcja CvInitProvider | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a5a8a9e70c85563e95037c754c59b6077ed21f28
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188799"
---
# <a name="cvinitprovider-function"></a>CvInitProvider — Funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Inicjuje dostawcę znaczników narzędzia. Musi zostać wywołana przed wszystkie inne funkcje SDK narzędzia Concurrency Visualizer.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pGuid`  
 Identyfikator guid dostawcy. Nie może mieć wartości NULL.  
  
 `ppProvider`  
 Adres zmiennej danych wyjściowych, który będzie przechowywał kontekstu dostawcy. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 Pomyślnie zainicjowano dostawcy lub kod błędu w przypadku zostały wszystkie błędy, S_OK. Aby sprawdzić, czy warunek błędu, należy użyć makra Powodzenie/niepowodzenie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkers.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)
