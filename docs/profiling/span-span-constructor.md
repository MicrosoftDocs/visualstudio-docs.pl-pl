---
title: 'span:: span — Konstruktor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a813506e64242d1effdb9ed64d35c9ee5d31239
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949977"
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

`_Series` Prawidłowy kontekst serii znaczników.

`_Format` Ciąg formatu złożonego, który zawiera tekst, który jest przemieszany z zerem lub więcej elementów formatu, który odpowiada obiektom na liście argumentów.

`_Importance` Poziom ważności.

`_Category` Kategorii.

## <a name="requirements"></a>Wymagania

**Nagłówek:** *cvmarkersobj. h*

**Przestrzeń nazw:** Współbieżność::d przesła

## <a name="see-also"></a>Zobacz też

- [span — Klasa](../profiling/span-class.md)