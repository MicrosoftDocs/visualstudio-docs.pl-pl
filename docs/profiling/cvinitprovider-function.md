---
title: Funkcja CvInitProvider | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a97be63cd782397e984fd8dbce7da844efa07540
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56626846"
---
# <a name="cvinitprovider-function"></a>Cvinitprovider — funkcja
Inicjuje dostawcę znaczników narzędzia. Musi zostać wywołana przed wszystkie inne funkcje SDK narzędzia Concurrency Visualizer.

## <a name="syntax"></a>Składnia

```C
HRESULT CvInitProvider(
   _In_ const GUID* pGuid,
   _Out_ PCV_PROVIDER* ppProvider
);
```

#### <a name="parameters"></a>Parametry
 `pGuid` Identyfikator guid dostawcy. Nie może mieć wartości NULL.

 `ppProvider` Adres zmiennej danych wyjściowych, który będzie przechowywał kontekstu dostawcy. Nie może mieć wartości NULL.

## <a name="return-value"></a>Wartość zwracana
 Pomyślnie zainicjowano dostawcy lub kod błędu w przypadku zostały wszystkie błędy, S_OK. Aby sprawdzić, czy warunek błędu, należy użyć makra Powodzenie/niepowodzenie.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers.h*

## <a name="see-also"></a>Zobacz także
- [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)