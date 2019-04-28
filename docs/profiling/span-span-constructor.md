---
title: Konstruktor span::span | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979825"
---
# <a name="spanspan-constructor"></a>span::span — Konstruktor

Inicjuje nowe wystąpienie klasy `span` klasy.

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

`_Series` Kontekst serii prawidłowe znacznika.

`_Format` Ciąg formatu złożonego, który zawiera tekst zmieszać z zero lub więcej elementów formatu, które odnoszą się do obiektów na liście argumentów.

`_Importance` Poziom ważności.

`_Category` Kategoria.

## <a name="requirements"></a>Wymagania

**Nagłówek:** *cvmarkersobj.h*

**Namespace:** CONCURRENCY::Diagnostic —

## <a name="see-also"></a>Zobacz także

- [span, klasa](../profiling/span-class.md)