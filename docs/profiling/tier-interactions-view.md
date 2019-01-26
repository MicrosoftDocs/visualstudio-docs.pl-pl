---
title: Widok interakcji warstwy | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.tierinteraction
helpviewer_keywords:
- Tier Interactions view
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 924f6ba126ab4663d6daa7b3744102b2365d521b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982146"
---
# <a name="tier-interactions-view"></a>Widok interakcji warstwowych

Profilowanie interakcji pomiędzy warstwami zawiera dodatkowe informacje o czasy wykonania w funkcjach aplikacji wielowarstwowych, które komunikują się z bazami danych za pośrednictwem [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]. Dane są zbierane tylko w przypadku wywołania funkcji synchronicznej.

**Wymagania**

- Visual Studio Enterprise

Widok interakcji wyświetla dane interakcji między warstwami na dwa okienka:

- W okienku głównym jest drzewa hierarchicznego. Wiersz najwyższego poziomu zawiera zagregowane dane dotyczące połączeń bazy danych [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] strony lub procesu. Węzły podrzędne zawierają zagregowane dane dotyczące połączenia bazy danych elementu nadrzędnego.

- Po kliknięciu węzła wywołania bazy danych w okienku głównym, dane wystąpienia wywołanie bazy danych są wyświetlane w okienku szczegółów.

  Czas jest wyświetlany jako liczbę milisekund lub liczby taktów zegara procesora CPU. Aby zmienić jednostkę czasu, wyświetlany, kliknij przycisk **narzędzia** menu, kliknij przycisk **opcje**, a następnie wybierz jedno z **Pokaż czas wartości w formie** opcje.

## <a name="master-pane"></a>W okienku głównym

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|— W przypadku wiersza najwyższego poziomu, nazwa PROFILOWANEGO procesu lub strony sieci Web.<br />– W przypadku wiersza połączenia bazy danych, nazwę serwera, który jest hostem bazy danych.|
|**Baza danych**|Nazwa bazy danych (tylko wiersze połączenia bazy danych).|
|**Liczba**|Całkowita liczba żądań, które są generowane przez proces, strony sieci Web lub połączenia z bazą danych.|
|**Łączny czas, który upłynął**|Całkowity czas spędzony na wykonywaniu każde żądanie jeden z procesów, strony sieci Web lub połączenia z bazą danych.|
|**Maksymalny czas, który upłynął**|Maksymalny czas poświęcony na wykonanie dowolnego jedno żądanie z procesu, strony sieci Web lub połączenia z bazą danych.|
|**Minimalny czas trwania**|Minimalny czas spędzony na wykonywaniu każde żądanie jeden z procesów, strony sieci Web lub połączenia z bazą danych.|
|**Średni czas trwania**|Średni czas spędzony na wykonywaniu żądania z procesu, strony sieci Web lub połączenia z bazą danych.|

## <a name="database-connection-details-pane"></a>W okienku szczegółów połączenia bazy danych

|Kolumna|Opis|
|------------|-----------------|
|**Tekst polecenia**|Zapytanie SQL żądania.|
|**Liczba zapytań**|Liczba przypadków, gdy zapytanie zostało uruchomione.|
|**Łączny czas, który upłynął**|Całkowity czas spędzony na wykonywaniu wystąpień zapytania.|
|**Maksymalny czas, który upłynął**|Maksymalny czas spędzony na wykonywaniu wszelkie jedno wystąpienie zapytania.|
|**Minimalny czas trwania**|Minimalny czas spędzony na wykonywaniu wszelkie jedno wystąpienie zapytania.|
|**Średni czas trwania**|Średni czas spędzony na wykonywaniu wystąpienie zapytania.|