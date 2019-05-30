---
title: Funkcja SccUninitialize | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f71e34352150143c7db207ed31ea6e879f97ca18
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338496"
---
# <a name="sccuninitialize-function"></a>SccUninitialize, funkcja
Ta funkcja czyści wszystkie alokacje lub otwartych połączeń utworzonych przez poprzednie wywołanie [SccInitialize](../extensibility/sccinitialize-function.md) w ramach przygotowania do zamykania wtyczka do kontroli źródła.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parametry
 pvContext

[in] Wskaźnik do struktury kontekście wtyczki kontroli źródła, utworzone w [SccInitialize](../extensibility/sccinitialize-function.md).

## <a name="return-value"></a>Wartość zwracana
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Oczyszczania została ukończona pomyślnie.|

## <a name="remarks"></a>Uwagi
 Wtyczka do kontroli źródła jest odpowiedzialny za przygotowywanie zamknięcie i zwalnianie pamięci, że wtyczka została przydzielona w strukturze kontekstu. Funkcja jest wywoływana raz dla każdego wystąpienia danego dodatku typu plug-in. Wywołanie [SccInitialize](../extensibility/sccinitialize-function.md) poprzedza tego wywołania. Brak projektów nadal może być otwarty w momencie wywołania `SccUninitialize`.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)