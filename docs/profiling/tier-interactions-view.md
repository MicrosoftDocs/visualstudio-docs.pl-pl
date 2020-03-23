---
title: Widok interakcji warstwy | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778144"
---
# <a name="tier-interactions-view"></a>Widok interakcji warstwowych

Profilowanie interakcji warstwy zawiera dodatkowe informacje na temat czasów wykonywania w [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]funkcjach aplikacji wielopoziomowych, które komunikują się z bazami danych za pośrednictwem . Dane są zbierane tylko dla wywołań funkcji synchronicznych.

**Wymagania**

- Visual Studio Enterprise

Widok interakcji wyświetla dane interakcji warstwy w dwóch okienkach:

- Okienko główne jest drzewem hierarchicznym. Wiersz najwyższego poziomu zawiera zagregowane dane [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dla połączeń z bazą danych strony lub procesu. Węzły podrzędne zawierają zagregowane dane dla połączeń bazy danych nadrzędnego.

- Po kliknięciu węzła wywołania bazy danych w okienku głównym dane dla wystąpienia wywołania bazy danych są wyświetlane w okienku szczegółów.

  Czas jest wyświetlany jako liczba milisekund lub liczba znaczników zegara procesora CPU. Aby zmienić wyświetlaną jednostkę czasu, kliknij menu **Narzędzia,** kliknij polecenie **Opcje**, a następnie wybierz jedną z **opcji Pokaż czas jako** opcje.

## <a name="master-pane"></a>Okienko wzorca

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|- W wierszu najwyższego poziomu nazwa profilowanego procesu lub strony sieci Web.<br />- Dla wiersza połączenia bazy danych, nazwa serwera, który obsługuje bazę danych.|
|**baza danych**|Nazwa bazy danych (tylko wiersze połączenia z bazą danych).|
|**Liczba**|Całkowita liczba żądań generowanych przez proces, stronę sieci Web lub połączenie z bazą danych.|
|**Całkowity czas, jaki upłynął**|Całkowity czas spędzony na wykonywaniu jednego żądania z procesu, strony sieci Web lub połączenia z bazą danych.|
|**Maksymalny czas, który upłynął**|Maksymalny czas wykonywania jednego żądania z procesu, strony sieci Web lub połączenia z bazą danych.|
|**Min. Czas, który upłynął**|Minimalny czas, jaki jest wykonywany przez jedno żądanie z procesu, strony sieci Web lub połączenia z bazą danych.|
|**Średni czas, który upłynął**|Średni czas wykonywania żądania z procesu, strony sieci Web lub połączenia z bazą danych.|

## <a name="database-connection-details-pane"></a>Okienko Szczegóły połączenia z bazą danych

|Kolumna|Opis|
|------------|-----------------|
|**Tekst polecenia**|Kwerenda SQL żądania.|
|**Liczba zapytań**|Liczba uruchomiono kwerendę.|
|**Całkowity czas, jaki upłynął**|Całkowity czas spędzony na wykonywaniu wystąpień kwerendy.|
|**Maksymalny czas, który upłynął**|Maksymalny czas, który jest spędzony na wykonywaniu jednego wystąpienia kwerendy.|
|**Min. Czas, który upłynął**|Minimalny czas, który jest spędzany na wykonywaniu jednego wystąpienia kwerendy.|
|**Średni czas, który upłynął**|Średni czas spędzony na wykonywaniu wystąpienia kwerendy.|
