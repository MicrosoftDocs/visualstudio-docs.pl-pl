---
description: Inicjuje nowe wystąpienie klasy marker_series.
title: 'marker_series:: marker_series — Konstruktor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::marker_series
helpviewer_keywords:
- Concurrency, diagnostic::marker_series constructor
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 88d82c78bc6126f6b3d96b77b39c729c4f452a28
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223982"
---
# <a name="marker_seriesmarker_series-constructor"></a>marker_series:: marker_series, Konstruktor
Inicjuje nowe wystąpienie klasy `marker_series`.

## <a name="syntax"></a>Składnia

```cpp
marker_series();
marker_series(
   _In_ LPCTSTR _SeriesName
);
marker_series(
   _In_ const GUID* _ProviderGuid
);
marker_series(
   _In_ const GUID* _ProviderGuid,
   _In_ LPCTSTR _SeriesName
);
```

#### <a name="parameters"></a>Parametry
 `_SeriesName` Nazwa serii do utworzenia.

 `_ProviderGuid` Identyfikator GUID dostawcy serii.

## <a name="requirements"></a>Wymagania
 **Nagłówek:** *cvmarkersobj. h*

 **Przestrzeń nazw:** Współbieżność::d przesła

## <a name="see-also"></a>Zobacz też
- [Klasa marker_series](../profiling/marker-series-class.md)
