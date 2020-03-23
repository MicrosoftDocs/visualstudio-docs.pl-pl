---
title: marker_series::Metoda write_alert | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert
helpviewer_keywords:
- Concurrency::diagnostic:marker_series::write_alert method
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 635f767f97ea3d237aeff843e99735eccae31efc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62831387"
---
# <a name="marker_serieswrite_alert-method"></a>marker_series::metoda write_alert
Zapisuje alert do pliku śledzenia wizualizatora współbieżności.

## <a name="syntax"></a>Składnia

```cpp
void write_alert(
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parametry
 `_Format`Ciąg formatu złożonego, który zawiera tekst połączony z elementami formatu zero lub więcej, które odpowiadają obiektom na liście argumentów.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkersobj.h*

 **Obszar nazw:** Współbieżność::dignostyk

## <a name="see-also"></a>Zobacz też
- [klasa marker_series](../profiling/marker-series-class.md)