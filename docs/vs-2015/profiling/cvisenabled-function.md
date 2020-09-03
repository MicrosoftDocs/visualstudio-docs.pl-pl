---
title: Funkcja Cvisenabled — | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177780"
---
# <a name="cvisenabled-function"></a>CvIsEnabled — Funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa, czy dla każdej sesji włączono określonego dostawcę ETW.  
  
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
 Kategorii.  
  
 `level`  
 Poziom ważności.  
  
 `pProvider`  
 Prawidłowy obiekt dostawcy. Nie może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli dostawca jest obecnie włączony. S_FALSE, jeśli dostawca jest obecnie wyłączony. Kod błędu w przypadku wystąpienia błędów. Aby sprawdzić warunek błędu, użyj makra zakończonego niepowodzeniem, a następnie sprawdź, czy S_OK/S_FALSE.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cvmarkers. h  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja biblioteki C++](../profiling/cpp-library-reference.md)
