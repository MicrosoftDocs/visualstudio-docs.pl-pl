---
title: marker_series::Metoda write_message | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::write_message
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_message method
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be6194936264d6038c4dc1e26b5d05f539f0dc6a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62830905"
---
# <a name="marker_serieswrite_message-method"></a>marker_series::metoda write_message
Zapisuje komunikat do pliku śledzenia wizualizatora współbieżności.

## <a name="syntax"></a>Składnia

```cpp
void write_message(
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
void write_message(
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parametry
 `_Format`Ciąg formatu złożonego, który zawiera tekst połączony z elementami formatu zero lub więcej, które odpowiadają obiektom na liście argumentów.

 `_Importance`Poziom ważności.

 `_Category`Category.Poziom ważności.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkersobj.h*

 **Obszar nazw:** Współbieżność::dignostyk

## <a name="see-also"></a>Zobacz też
- [klasa marker_series](../profiling/marker-series-class.md)