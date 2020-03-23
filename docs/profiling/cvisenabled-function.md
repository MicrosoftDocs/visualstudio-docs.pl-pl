---
title: Funkcja CvIsEnabled | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 92763e352d04d5aa3e88a68bad7adfcd05897027
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62945417"
---
# <a name="cvisenabled-function"></a>Funkcja CvIsEnabled
Określa, czy którakolwiek z sesji włączyła określonego dostawcę ETW.

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
 `category`Kategorii.

 `level`Poziom ważności.

 `pProvider`Prawidłowy obiekt dostawcy. Nie może być null.

## <a name="return-value"></a>Wartość zwracana
 S_OK, jeśli dostawca jest obecnie włączony. S_FALSE, jeśli dostawca jest obecnie wyłączony. Kod błędu w przypadku wystąpienia błędów. Użyj makra FAILED, aby sprawdzić stan błędu, a następnie sprawdź, czy S_OK/S_FALSE.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers.h*

## <a name="see-also"></a>Zobacz też
- [Odwołanie do biblioteki języka C++](../profiling/cpp-library-reference.md)