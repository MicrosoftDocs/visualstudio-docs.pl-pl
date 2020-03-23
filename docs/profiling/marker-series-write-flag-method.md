---
title: marker_series::Metoda write_flag | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersojb/Concurrency::diagnostic::marker_series::write_flag
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_flag method
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f09cca9bd1e3babccb0debc369881a0efa00fa0b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62830814"
---
# <a name="marker_serieswrite_flag-method"></a>marker_series::metoda write_flag
Zapisuje flagę do pliku śledzenia wizualizatora współbieżności.

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
 `_Format`Ciąg formatu złożonego, który zawiera tekst połączony z elementami formatu zero lub więcej, które odpowiadają obiektom na liście argumentów.

 `_Importance`Poziom ważności.

 `_Category`Kategorii.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkersobj.h*

 **Obszar nazw:** Współbieżność::dignostyk

## <a name="see-also"></a>Zobacz też
- [klasa marker_series](../profiling/marker-series-class.md)