---
title: Funkcja CvIsEnabled | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ba30f3ab75504c0115b8a881f2014910f3b9fd0b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771001"
---
# <a name="cvisenabled-function"></a>CvIsEnabled — Funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa, czy dowolnej sesji ma włączone określonego dostawcy funkcji ETW.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 **Nagłówek:** cvmarkers.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)
