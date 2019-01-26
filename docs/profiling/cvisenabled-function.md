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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8af4da802ef0ad87831f2f67f47e8ffb66a969e7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990046"
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