---
title: rozpiętość::konstruktor zakresu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f761e87c1658c11bfdfd93a4f4e22299d88575a8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62979825"
---
# <a name="spanspan-constructor"></a>span::span — Konstruktor

Inicjuje nowe wystąpienie klasy `span`.

## <a name="syntax"></a>Składnia

```cpp
span(
   const marker_series& _Series,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parametry

`_Series`Prawidłowy kontekst serii znaczników.

`_Format`Ciąg formatu złożonego, który zawiera tekst połączony z elementami formatu zero lub więcej, które odpowiadają obiektom na liście argumentów.

`_Importance`Poziom ważności.

`_Category`Kategorii.

## <a name="requirements"></a>Wymagania

**Nagłówek:** *cvmarkersobj.h*

**Obszar nazw:** Współbieżność::dignostyk

## <a name="see-also"></a>Zobacz też

- [klasa span](../profiling/span-class.md)