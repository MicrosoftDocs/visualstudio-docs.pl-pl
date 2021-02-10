---
title: Widok interakcji między warstwami | Microsoft Docs
description: Dowiedz się, jak profilowanie interakcji między warstwami zawiera informacje o czasach wykonywania w funkcjach aplikacji wielowarstwowych komunikujących się z bazami danych.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.tierinteraction
helpviewer_keywords:
- Tier Interactions view
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 350810bba477f5a86963862fb496cf05eaf2c810
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963188"
---
# <a name="tier-interactions-view"></a>Widok interakcji warstwowych

Profilowanie interakcji między warstwami zawiera dodatkowe informacje o czasach wykonywania w funkcjach aplikacji wielowarstwowych komunikujących się z bazami danych za pomocą programu [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] . Dane są zbierane tylko dla wywołań funkcji synchronicznych.

**Wymagania**

- Visual Studio Enterprise

Widok Interakcje wyświetla dane interakcji warstwy w dwóch okienkach:

- Okienko główne jest drzewem hierarchicznym. Wiersz najwyższego poziomu zawiera zagregowane dane dla połączeń bazy danych na [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] stronie lub w procesie. Węzły podrzędne zawierają zagregowane dane dla połączeń bazy danych nadrzędnych.

- Po kliknięciu węzła wywołanie bazy danych w okienku głównym dane wystąpienia wywołania bazy danych są wyświetlane w okienku szczegółów.

  Czas jest wyświetlany jako liczba milisekund lub liczba taktów zegara procesora. Aby zmienić wyświetlaną jednostkę czasu, kliknij menu **Narzędzia** , kliknij pozycję **Opcje**, a następnie wybierz jedną z opcji **Pokaż wartości czasu jako** opcje.

## <a name="master-pane"></a>Okienko główne

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|— Dla wiersza najwyższego poziomu nazwa profilowanego procesu lub strony sieci Web.<br />— Dla wiersza połączenie z bazą danych nazwa serwera, który hostuje bazę danych programu.|
|**Database** (Baza danych)|Nazwa bazy danych (tylko wiersze połączenia bazy danych).|
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
