---
description: Zapisuje flagę w pliku śledzenia Concurrency Visualizer.
title: 'marker_series:: write_flag Metoda | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersojb/Concurrency, diagnostic::marker_series::write_flag
helpviewer_keywords:
- Concurrency, diagnostic::marker_series::write_flag method
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5223c466674ba0d7d623cc33a3989d359bbabea2
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223891"
---
# <a name="marker_serieswrite_flag-method"></a>marker_series:: write_flag, Metoda
Zapisuje flagę w pliku śledzenia Concurrency Visualizer.

## <a name="syntax"></a>Składnia

```cpp
void write_flag(
   _In_ LPCTSTR _Format,
   ...
);
void write_flag(
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
void write_flag(
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
void write_flag(
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parametry
 `_Format` Ciąg formatu złożonego, który zawiera tekst, który jest przemieszany z zerem lub więcej elementów formatu, który odpowiada obiektom na liście argumentów.

 `_Importance` Poziom ważności.

 `_Category` Kategorii.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkersobj. h*

 **Przestrzeń nazw:** Współbieżność::d przesła

## <a name="see-also"></a>Zobacz też
- [Klasa marker_series](../profiling/marker-series-class.md)
