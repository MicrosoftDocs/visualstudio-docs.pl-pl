---
title: Cvleavespan — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvLeaveSpan
helpviewer_keywords:
- CvLeaveSpan method
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe234d60e8cd86279d3dcc01da95e6d2e6202213
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749161"
---
# <a name="cvleavespan-function"></a>Cvleavespan — funkcja
Oznacza koniec zakresu.  
  
## <a name="syntax"></a>Składnia  
  
```C  
HRESULT CvLeaveSpan(  
   _In_ PCV_SPAN pSpan  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSpan`  
 Obiekt zakresu zwrócony przez poprzednie wywołanie cventerspan — *. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość S_OK, gdy wiadomość zostanie pomyślnie zapisany. Kod błędu w przypadku, gdy było żadnych błędów. Użyj makra powiodło się/nie powiodło się, aby sprawdzić warunku błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** *cvmarkers.h*  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do biblioteki C++](../profiling/cpp-library-reference.md)