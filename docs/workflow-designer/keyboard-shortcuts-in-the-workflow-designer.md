---
title: Projektant przepływu pracy — skróty klawiaturowe w Projektancie przepływu pracy
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 95e42442e8dce5db1ef6b670043bf1f26e554773
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62537104"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Skróty klawiaturowe w Projektancie przepływu pracy

Wszystkie podstawowe funkcje projektanta przepływów pracy są dostępne przez klawiatury.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Nawigowanie w Projektancie przepływu pracy za pomocą klawiatury

W programie Visual Studio globalne skróty i debugowania skróty są stosowane do projektanta przepływów pracy. Ponadto liczba określonych skrótów klawiaturowych projektanta przepływów pracy zostały utworzone. W programie Visual Studio wszystkie skróty klawiaturowe mogą być ponownie mapowany. Jednak w rehostowanym aplikacji, skróty klawiaturowe są zapisane na stałe.

### <a name="workflow-designer-keyboard-shortcuts"></a>Skróty klawiaturowe w Projektancie przepływu pracy

W poniższej tabeli przedstawiono domyślne skróty klawiaturowe, przypisany do poleceń projektanta przepływów pracy.

|Skrót|Cel|
|-|-------------|
|CTRL+E, A|Pokazuje lub ukrywa projektanta argumentów.|
|CTRL+E, C|Zwija wybrane działanie w miejscu.|
|CTRL+E, E|Rozwija wybrane działanie w miejscu.|
|CTRL+E, F|Łączy wybrane działania w elemencie Schemat blokowy.|
|CTRL+E, I|Pokazuje lub ukrywa projektanta importów.|
|CTRL+E, M|Przenosi fokus klawiatury do następnego elementu w kolejności tabulacji.|
|CTRL+E, N|Tworzy nową zmienną zakresu wybranego działania (lub najbardziej).|
|CTRL+E, O|Pokazuje lub ukrywa mapowanie przeglądów.|
|CTRL+E, P|Powoduje przejście do elementu nadrzędnego wybranego działania. Przechodzi w górę o jeden poziom w nadrzędnych i zmienia działanie główne na powierzchni projektowej.|
|CTRL+E, S|Dodaje element z fokusem klawiatury do bieżącego zaznaczenia.|
|CTRL+E, V|Pokazuje lub ukrywa projektanta zmiennych.|
|CTRL+E, X|Rozwija wszystkie działania w przepływie pracy.|
|CTRL+ALT+F6|Przenosi fokus klawiatury z bieżącego obszaru interfejsu użytkownika do obszaru dalej w sekwencji. Kolejność jest następująca:<br /><br /> 1.  Pasek nawigacyjny łączy do stron nadrzędnych.<br />2.  Powierzchnia projektowa<br />3.  Projektanta argumentów/zmienne/importów, jeśli jest otwarty<br />4.  Powłoka|

### <a name="flowchart"></a>Schemat blokowy

Na poniższej liście przedstawiono gestów, używaną do utworzenia schematu blokowego klawiatury. Tak jak w pozostałej części projektanta przepływów pracy działania są dodawane do powierzchni projektanta za pomocą skrótów globalnego przybornika dostarczane z programem Visual Studio.

- Aby przenieść działania, wybierz działanie, a następnie używaj klawiszy strzałek Aby zmienić położenie.

- Aby zmienić rozmiar blokowego, Przenieś działanie poza granicą bieżącego schematu blokowego, używając klawiszy ze strzałkami. Schemat blokowy zmieniany jest automatycznie.

- Aby ustawić działanie jako węzeł początkowy, użyj **ustawiony jako Węzeł_początkowy** polecenia w menu kontekstowym.

- Aby połączyć działania:

    1. Wybierz czynność źródła, przechodząc do działania.

    2. Naciśnij klawisze CTRL + E, M tyle razy, zgodnie z potrzebami, aby przenieść fokus klawiatury na działanie docelowe.

    3. Naciśnij klawisze CTRL + E, S, aby dodać działanie docelowe do wyboru.

    4. Naciśnij klawisze CTRL + E, F, aby dodać łącznika ze źródła do miejsca docelowego.

Uwagi dotyczące łączenia działań przez klawiatury:

- Aby włączyć wiele połączeń w tym samym czasie, dodając więcej działań do wyboru przed naciskając klawisze CTRL + E, F. Połączenia są nawiązywane w kolejności, czy działania zostały dodane do zaznaczenia.

- Jeśli nie można połączyć dwa działania na przykład jeśli działania źródłowego ma już połączenia wychodzącego inne połączenia między działaniami w zaznaczeniu nadal zostały wprowadzone, jeśli to możliwe.

- Gdy **FlowDecision** jest dołączony do zaznaczenia i **FlowDecision** ma Brak wychodzących łączników, łącznik jest umieszczany na **True** gałęzi.

### <a name="expression-editing"></a>Edytowanie wyrażeń

Domyślnie w edytorze wyrażeń w Projektancie przepływu pracy, zastosowanie mają poniższe ograniczenia mają zastosowanie domyślne skróty klawiaturowe do edycji tekstu w języku Visual Basic:

- Ponowne mapowanie skróty klawiaturowe dla następujących poleceń nie ma znaczenia. Domyślne skróty klawiaturowe można używać tylko dostępu do tych poleceń podczas edycji wyrażenia.

   - Wytnij
   - Kopiuj
   - Wklej
   - Zaznacz wszystko
   - Cofnij
   - Wykonaj ponownie

- Aby ponownie zamapować skróty klawiaturowe dla poleceń edycji wyrażenia w Projektancie przepływu pracy w programie Visual Studio, należy edytować skróty w zakresie projektanta przepływów pracy. Zmiany wprowadzone w zakresie Edytor tekstu nie automatycznie dotyczą projektanta przepływów pracy. Jeśli chcesz ponownie zmapować skróty w obu miejscach, należy najpierw zastosować zmiany dwukrotnie (raz dla każdego zakresu).