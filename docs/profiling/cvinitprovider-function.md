---
title: Funkcja CvInitProvider — | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: b06190568454977bfcb54d65db9011fc979f7591
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329568"
---
# <a name="cvinitprovider-function"></a>CvInitProvider —, funkcja
Inicjuje dostawcę znaczników. Musi być wywoływana przed innymi funkcjami zestawu SDK wizualizatora współbieżności.

## <a name="syntax"></a>Składnia

```C
HRESULT CvInitProvider(
   _In_ const GUID* pGuid,
   _Out_ PCV_PROVIDER* ppProvider
);
```

#### <a name="parameters"></a>Parametry
 `pGuid`Identyfikator GUID dostawcy. Nie może mieć wartości NULL.

 `ppProvider`Adres zmiennej wyjściowej, w której będzie przechowywany kontekst dostawcy. Nie może mieć wartości NULL.

## <a name="return-value"></a>Wartość zwracana
 S_OK, gdy dostawca został pomyślnie zainicjowany lub kod błędu w przypadku wystąpienia błędów. Aby sprawdzić warunek błędu, użyj makr zakończonych powodzeniem i zakończonych niepowodzeniem.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkers. h*

## <a name="see-also"></a>Zobacz też
- [Dokumentacja biblioteki C++](../profiling/cpp-library-reference.md)