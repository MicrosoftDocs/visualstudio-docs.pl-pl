---
title: Funkcja CvInitProvider | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62552670"
---
# <a name="cvinitprovider-function"></a>Funkcja CvInitProvider
Inicjuje dostawcę znaczników. Musi być wywołana przed innymi funkcjami SDK wizualizatora współbieżności.

## <a name="syntax"></a>Składnia

```C
HRESULT CvInitProvider(
   _In_ const GUID* pGuid,
   _Out_ PCV_PROVIDER* ppProvider
);
```

#### <a name="parameters"></a>Parametry
 `pGuid`Identyfikator guid dostawcy. Nie może być null.

 `ppProvider`Adres zmiennej wyjściowej, która będzie przechowywać kontekst dostawcy. Nie może być null.

## <a name="return-value"></a>Wartość zwracana
 S_OK, gdy dostawca został pomyślnie zainicjowany lub kod błędu w przypadku wystąpienia błędów. Użyj makr UDANE/NIEUDANE, aby sprawdzić, czy nie ma warunku błędu.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers.h*

## <a name="see-also"></a>Zobacz też
- [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)