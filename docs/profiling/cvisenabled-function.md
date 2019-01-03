---
title: Funkcja CvIsEnabled | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c35fc883e53e1b1cc430724d87d8bcbd1bb32ee
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989193"
---
# <a name="cvisenabled-function"></a>Cvisenabled — funkcja
Określa, czy dowolnej sesji ma włączone określonego dostawcy funkcji ETW.  
  
## <a name="syntax"></a>Składnia  
  
```C  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `category`  
 Kategoria.  
  
 `level`  
 Poziom ważności.  
  
 `pProvider`  
 Obiekt dostawcy prawidłowe. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli dostawca jest obecnie włączona. S_FALSE, jeśli dostawca jest obecnie wyłączona. Kod błędu w przypadku, gdy było żadnych błędów. Aby Sprawdź, czy warunek błędu, a następnie wyszukaj S_OK/S_FALSE, należy użyć makra nie powiodło się.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** *cvmarkers.h*  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)