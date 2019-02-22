---
title: Funkcja CvReleaseProvider | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0008b7476290558c098b2241fde5c9b209933a0a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56606761"
---
# <a name="cvreleaseprovider-function"></a>Cvreleaseprovider — funkcja
Dostawca znacznika wydań. Zwalnianie dostawcy znacznika nie wpłynie na utworzonej wcześniej znaczników serii tego dostawcy. Seria znacznika musi to być wersja osobno przez wywołanie cvreleasemarkerseries —. Nie można zwolnić dostawcy powoduje, że przeciek pamięci.

## <a name="syntax"></a>Składnia

```C
HRESULT CvReleaseProvider(
   _In_ PCV_PROVIDER pProvider
);
```

#### <a name="parameters"></a>Parametry
 `pProvider` Kontekst dostawcy. Nie może mieć wartości NULL.

## <a name="return-value"></a>Wartość zwracana
 S_OK, gdy dostawca jest pomyślnie zwolnione lub kod błędu w przypadku zostały wszystkie błędy. Aby sprawdzić, czy warunek błędu, należy użyć makra Powodzenie/niepowodzenie.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers.h*

## <a name="see-also"></a>Zobacz także
- [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)