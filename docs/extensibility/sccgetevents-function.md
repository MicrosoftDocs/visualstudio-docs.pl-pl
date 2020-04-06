---
title: Funkcja SccGetEvents | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91b3debf0e686ceece3048cf3d92b629e3359edd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700816"
---
# <a name="sccgetevents-function"></a>SccGetEvents, funkcja
Ta funkcja pobiera zdarzenie stanu w kolejce.

## <a name="syntax"></a>Składnia

```cpp
SCCRTN SccGetEvents (
   LPVOID pvContext,
   LPSTR  lpFileName,
   LPLONG lpStatus,
   LPLONG pnEventsRemaining
);
```

### <a name="parameters"></a>Parametry
 pvContext

[w] Struktura kontekstu wtyczki formantu źródła.

 lpFileName

[w, na zewnątrz] Bufor, w którym wtyczka kontroli źródła umieszcza zwróconą nazwę pliku (do _MAX_PATH znaków).

 lpStatus

[w, na zewnątrz] Zwraca kod stanu (zobacz [Kod stanu pliku](../extensibility/file-status-code-enumerator.md) dla możliwych wartości).

 pnEventsReaining

[w, na zewnątrz] Zwraca liczbę wpisów pozostałych w kolejce po tym wywołaniu. Jeśli ten numer jest duży, wywołujący może podjąć decyzję o wywołaniu [SccQueryInfo,](../extensibility/sccqueryinfo-function.md) aby uzyskać wszystkie informacje naraz.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Powiększyć powodz.|
|SCC_E_OPNOTSUPPORTED|Ta funkcja nie jest obsługiwana.|
|SCC_E_NONSPECIFICERROR|Niespecyficzna awaria.|

## <a name="remarks"></a>Uwagi
 Ta funkcja jest wywoływana podczas przetwarzania bezczynności, aby sprawdzić, czy nie było żadnych aktualizacji stanu dla plików pod kontrolą źródła. Wtyczka kontroli źródła zachowuje stan wszystkich plików, o których wie, a za każdym razem, gdy zmiana stanu zostanie odnotowana przez wtyczkę, stan i skojarzony plik są przechowywane w kolejce. Po `SccGetEvents` wywołaniu górny element kolejki jest pobierany i zwracany. Ta funkcja jest ograniczona do zwracania tylko wcześniej buforowanych informacji i musi mieć bardzo szybki zwrot (to oznacza, że nie odczytuje dysku lub prosi o stan systemu kontroli źródła); w przeciwnym razie wydajność IDE może zacząć się obniżać.

 Jeśli nie ma aktualizacji stanu do raportu, wtyczka formantu źródła przechowuje pusty ciąg w buforze wskazywowym przez `lpFileName`. W przeciwnym razie wtyczka przechowuje pełną nazwę ścieżki pliku, dla którego informacje o stanie uległy zmianie, i zwraca odpowiedni kod stanu (jedną z wartości wyszczególnionych w [kodzie stanu pliku](../extensibility/file-status-code-enumerator.md)).

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki sterowania źródłem](../extensibility/source-control-plug-in-api-functions.md)
- [Kod stanu pliku](../extensibility/file-status-code-enumerator.md)
