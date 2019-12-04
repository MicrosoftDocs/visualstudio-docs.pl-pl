---
title: Widok interakcji między warstwami | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.tierinteraction
helpviewer_keywords:
- Tier Interactions view
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d188d6c3268c8ee9f066eba1b6a57e469f34a78e
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778144"
---
# <a name="tier-interactions-view"></a>Widok interakcji warstwowych

Profilowanie interakcji między warstwami zawiera dodatkowe informacje o czasach wykonywania w funkcjach aplikacji wielowarstwowych komunikujących się z bazami danych za pomocą [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]. Dane są zbierane tylko dla wywołań funkcji synchronicznych.

**Requirements**

- Visual Studio Enterprise

Widok Interakcje wyświetla dane interakcji warstwy w dwóch okienkach:

- Okienko główne jest drzewem hierarchicznym. Wiersz najwyższego poziomu zawiera zagregowane dane dla połączeń z bazą danych [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] stronie lub procesu. Węzły podrzędne zawierają zagregowane dane dla połączeń bazy danych nadrzędnych.

- Po kliknięciu węzła wywołanie bazy danych w okienku głównym dane wystąpienia wywołania bazy danych są wyświetlane w okienku szczegółów.

  Czas jest wyświetlany jako liczba milisekund lub liczba taktów zegara procesora. Aby zmienić wyświetlaną jednostkę czasu, kliknij menu **Narzędzia** , kliknij pozycję **Opcje**, a następnie wybierz jedną z opcji **Pokaż wartości czasu jako** opcje.

## <a name="master-pane"></a>Okienko główne

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|— Dla wiersza najwyższego poziomu nazwa profilowanego procesu lub strony sieci Web.<br />— Dla wiersza połączenie z bazą danych nazwa serwera, który hostuje bazę danych programu.|
|**Database**|Nazwa bazy danych (tylko wiersze połączenia bazy danych).|
|**Liczbą**|Całkowita liczba żądań generowanych przez proces, stronę sieci Web lub połączenie z bazą danych.|
|**Łączny czas, który upłynął**|Łączny czas spędzony na wykonywaniu jednego żądania na podstawie procesu, strony sieci Web lub połączenia bazy danych.|
|**Maksymalny czas, który upłynął**|Maksymalny czas wykonywania jednego żądania na podstawie procesu, strony sieci Web lub połączenia z bazą danych.|
|**Minimalny czas, który upłynął**|Minimalny czas trwania każdego żądania z procesu, strony sieci Web lub połączenia bazy danych.|
|**Średni czas, który upłynął**|Średni czas poświęcany na wykonanie żądania na podstawie procesu, strony sieci Web lub połączenia z bazą danych.|

## <a name="database-connection-details-pane"></a>Okienko Szczegóły połączenia z bazą danych

|Kolumna|Opis|
|------------|-----------------|
|**Tekst polecenia**|Zapytanie SQL żądania.|
|**Liczba zapytań**|Liczba uruchomień zapytania.|
|**Łączny czas, który upłynął**|Łączny czas spędzony na wykonywaniu wystąpień zapytania.|
|**Maksymalny czas, który upłynął**|Maksymalny czas spędzony na wykonywaniu jednego wystąpienia zapytania.|
|**Minimalny czas, który upłynął**|Minimalny czas spędzony na wykonywaniu jednego wystąpienia zapytania.|
|**Średni czas, który upłynął**|Średni czas spędzony na wykonywaniu wystąpienia zapytania.|
