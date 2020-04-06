---
title: Funkcja SccUninitialize | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4706ddf28949af4fe1bba01c32b2c64c9156d51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700230"
---
# <a name="sccuninitialize-function"></a>SccUninitialize, funkcja
Ta funkcja czyści wszelkie alokacje lub otwarte połączenia utworzone przez poprzednie wywołanie [SccInitialize](../extensibility/sccinitialize-function.md) w ramach przygotowań do zamknięcia wtyczki kontroli źródła.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parametry
 pvContext

[w] Wskaźnik do struktury kontekstu wtyczki formantu źródła utworzonej w [SccInitialize](../extensibility/sccinitialize-function.md).

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Oczyszczanie zostało zakończone pomyślnie.|

## <a name="remarks"></a>Uwagi
 Wtyczka kontroli źródła jest odpowiedzialny za przygotowanie do zamknięcia i zwalniania pamięci, że dodatek przypisany do struktury kontekstu. Funkcja jest wywoływana raz dla każdego wystąpienia wtyczki. Wywołanie [SccInitialize](../extensibility/sccinitialize-function.md) poprzedza to wywołanie. Żadne projekty nie mogą być nadal otwarte `SccUninitialize`w momencie wezwania do .

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
