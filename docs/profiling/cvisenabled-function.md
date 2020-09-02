---
title: Funkcja Cvisenabled — | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 53de9ee136c9bd12c732339b4c1c8a223fe1a3ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330063"
---
# <a name="cvisenabled-function"></a>Cvisenabled —, funkcja
Określa, czy dla każdej sesji włączono określonego dostawcę ETW.

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
 `category` Kategorii.

 `level` Poziom ważności.

 `pProvider` Prawidłowy obiekt dostawcy. Nie może mieć wartości NULL.

## <a name="return-value"></a>Wartość zwracana
 S_OK, jeśli dostawca jest obecnie włączony. S_FALSE, jeśli dostawca jest obecnie wyłączony. Kod błędu w przypadku wystąpienia błędów. Aby sprawdzić warunek błędu, użyj makra zakończonego niepowodzeniem, a następnie sprawdź, czy S_OK/S_FALSE.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers. h*

## <a name="see-also"></a>Zobacz też
- [Dokumentacja biblioteki C++](../profiling/cpp-library-reference.md)