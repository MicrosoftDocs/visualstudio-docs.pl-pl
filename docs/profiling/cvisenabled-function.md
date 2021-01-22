---
title: Funkcja Cvisenabled — | Microsoft Docs
description: Zobacz informacje referencyjne dotyczące funkcji zestawu SDK wizualizatora współbieżności Cvisenabled — (biblioteka C).
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 57f1bb96480fe054c729b11a3fabd311407fa858
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686483"
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