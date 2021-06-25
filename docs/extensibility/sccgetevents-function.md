---
description: Ta funkcja pobiera zdarzenie stanu w kolejce.
title: SccGetEvents, funkcja | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9438ac10301e2da43b26a88575e44a8ad2c0bf82
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901061"
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

[in] Struktura kontekstu wtyczki kontroli źródła.

 lpFileName

[in, out] Bufor, w którym wtyczka kontroli kodu źródłowego umieszcza zwróconą nazwę pliku (do _MAX_PATH znaków).

 lpStatus

[in, out] Zwraca kod stanu (zobacz [Kod stanu pliku,](../extensibility/file-status-code-enumerator.md) aby uzyskać możliwe wartości).

 pnEventsRemaining

[in, out] Zwraca liczbę wpisów pozostawionych w kolejce po tym wywołaniu. Jeśli ta liczba jest duża, wywołujący może zdecydować się na wywołanie [SccQueryInfo](../extensibility/sccqueryinfo-function.md) w celu uzyskania wszystkich informacji jednocześnie.

## <a name="return-value"></a>Wartość zwracana
 Oczekuje się, że implementacja wtyczki kontroli źródła dla tej funkcji zwróci jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|SCC_OK|Pobierz zdarzenia zakończyły się pomyślnie.|
|SCC_E_OPNOTSUPPORTED|Ta funkcja nie jest obsługiwana.|
|SCC_E_NONSPECIFICERROR|Nieokreślona awaria.|

## <a name="remarks"></a>Uwagi
 Ta funkcja jest wywoływana podczas przetwarzania bezczynnego, aby sprawdzić, czy w plikach z kontrolą źródła były dostępne jakiekolwiek aktualizacje stanu. Wtyczka kontroli źródła zachowuje stan wszystkich plików, które zna, i za każdym razem, gdy wtyczka zanotuje zmianę stanu, stan i skojarzony plik są przechowywane w kolejce. Gdy `SccGetEvents` jest wywoływana, górny element kolejki jest pobierany i zwracany. Ta funkcja jest ograniczona do zwracania tylko wcześniej buforowanych informacji i musi mieć bardzo szybkie obracanie (to oznacza, że nie odczytuje dysku ani nie pyta o stan systemu kontroli źródła); w przeciwnym razie wydajność środowiska IDE może zacząć się pogarszać.

 Jeśli nie ma aktualizacji stanu raportu, wtyczka kontroli źródła przechowuje pusty ciąg w buforze wskazywanym przez element `lpFileName` . W przeciwnym razie wtyczka przechowuje pełną nazwę ścieżki pliku, dla którego informacje o stanie uległy zmianie, i zwraca odpowiedni kod stanu (jedną z wartości szczegółowych w [pliku kod stanu](../extensibility/file-status-code-enumerator.md)).

## <a name="see-also"></a>Zobacz też
- [Funkcje interfejsu API wtyczki kontroli kodu źródłowego](../extensibility/source-control-plug-in-api-functions.md)
- [Kod stanu pliku](../extensibility/file-status-code-enumerator.md)
