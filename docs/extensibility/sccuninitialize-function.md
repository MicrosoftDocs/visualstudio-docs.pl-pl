---
description: Ta funkcja czyści wszelkie alokacje lub otwarte połączenia utworzone przez poprzednie wywołanie funkcji SccInitialize w ramach przygotowania do zamknięcia wtyczki kontroli źródła.
title: SccUninitialize, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0d46aedd3e962d0684689ff29a34061b777fe08e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904077"
---
# <a name="sccuninitialize-function"></a>SccUninitialize, funkcja
Ta funkcja czyści wszelkie alokacje lub otwarte połączenia utworzone przez poprzednie wywołanie funkcji [SccInitialize](../extensibility/sccinitialize-function.md) w ramach przygotowania do zamknięcia wtyczki kontroli źródła.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parametry
 pvContext

[in] Wskaźnik do struktury kontekstu wtyczki kontroli źródła utworzonej w pliku [SccInitialize](../extensibility/sccinitialize-function.md).

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła dla tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Czyszczenie zostało ukończone pomyślnie.|

## <a name="remarks"></a>Uwagi
 Wtyczka kontroli źródła jest odpowiedzialna za przygotowanie do zamknięcia i zwalnianie pamięci przydzielonej przez wtyczkę do struktury kontekstu. Funkcja jest wywoływana raz dla każdego wystąpienia wtyczki. Wywołanie [SccInitialize](../extensibility/sccinitialize-function.md) poprzedza to wywołanie. W czasie wywołania do nadal nie można otworzyć żadnych `SccUninitialize` projektów.

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
