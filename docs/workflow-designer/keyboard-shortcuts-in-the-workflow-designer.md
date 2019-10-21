---
title: 'Projektant przepływu pracy: skróty klawiaturowe'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f36e8b6d67d2405fbc74c0b1bf854b3a3baaf4da
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650161"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Skróty klawiaturowe w Projektancie przepływu pracy

Wszystkie podstawowe funkcje Projektant przepływu pracy są dostępne na klawiaturze.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Nawigowanie Projektant przepływu pracy przy użyciu klawiatury

W programie Visual Studio globalne skróty i skróty debugowania stosują się do Projektant przepływu pracy. Ponadto zostały utworzone różne Projektant przepływu pracy skróty klawiaturowe. W programie Visual Studio można ponownie mapować wszystkie skróty klawiaturowe. Jednak w aplikacji przehostowanej te skróty klawiaturowe są stałe.

### <a name="workflow-designer-keyboard-shortcuts"></a>Skróty klawiaturowe Projektant przepływu pracy

Poniższa tabela podsumowuje domyślne skróty klawiaturowe przypisane do poleceń Projektant przepływu pracy.

|Skrót|Cel|
|-|-------------|
|CTRL + E, A|Pokazuje lub ukrywa projektanta argumentów.|
|CTRL + E, C|Zwija wybrane działanie.|
|CTRL + E, E|Rozwija wybrane działanie na miejscu.|
|CTRL + E, F|Łączy wybrane działania w schemacie blokowym.|
|CTRL + E, I|Pokazuje lub ukrywa projektanta importów.|
|CTRL + E, M|Przesuwa fokus klawiatury do następnego elementu w kolejności tabulacji.|
|CTRL + E, N|Tworzy nową zmienną w zakresie wybranego działania (lub najbliższą).|
|CTRL + E, O|Pokazuje lub ukrywa mapę przeglądu.|
|CTRL + E, P|Powoduje przejście do elementu nadrzędnego wybranego działania. Powoduje to przejście do jednego poziomu w nawigacji nawigacyjnej i zmianę działania głównego na powierzchni projektanta.|
|CTRL + E, S|Dodaje element z fokusem klawiatury do bieżącego zaznaczenia.|
|CTRL + E, V|Pokazuje lub ukrywa projektanta zmiennych.|
|CTRL + E, X|Rozwija wszystkie działania w przepływie pracy.|
|CTRL + ALT + F6|Przenosi fokus klawiatury z bieżącego obszaru interfejsu użytkownika do następnego obszaru w sekwencji. Kolejność jest następująca:<br /><br /> 1. pasek nawigacyjny.<br />2. powierzchnia projektanta<br />3. argumenty/zmienne/Importy projektant w przypadku otwarcia<br />4. Shell|

### <a name="flowchart"></a>Schemat blokowy

Na poniższej liście przedstawiono gesty używane do konstruowania schematu blokowego za pomocą klawiatury. Tak jak w pozostałej części Projektant przepływu pracy działania są dodawane do powierzchni projektanta przy użyciu globalnych skrótów przybornika dostępnych w programie Visual Studio.

- Aby przenieść działanie, wybierz działanie i użyj klawiszy strzałek, aby zmienić ich położenie.

- Aby zmienić rozmiar schematu blokowego, Przenieś działanie poza bieżącą krawędź schematu blokowego za pomocą klawiszy strzałek. Automatycznie zmieniany jest rozmiar schematu blokowego.

- Aby ustawić działanie jako węzeł początkowy, użyj polecenia **Set as parametr StartNode** w menu po kliknięciu prawym przyciskiem myszy.

- Aby połączyć działania:

    1. Wybierz działanie źródłowe, naciskając klawisz Tab do działania.

    2. Naciśnij klawisze CTRL + E, M tyle razy, ile jest to konieczne, aby przenieść fokus klawiatury do działania docelowego.

    3. Naciśnij klawisze CTRL + E, aby dodać działanie docelowe do zaznaczenia.

    4. Naciśnij klawisze CTRL + E, F, aby dodać łącznik ze źródła do miejsca docelowego.

Uwagi dotyczące łączenia działań według klawiatury:

- Można utworzyć wiele połączeń w tym samym czasie, dodając więcej działań do zaznaczenia przed naciśnięciem kombinacji klawiszy CTRL + E, F. Połączenia są wykonywane w kolejności, w jakiej działania zostały dodane do zaznaczenia.

- Jeśli para działań nie może być połączona, na przykład jeśli działanie źródłowe ma już połączenie wychodzące, inne połączenia między działaniami w ramach zaznaczenia nadal są wykonywane zawsze, gdy jest to możliwe.

- Gdy **FlowDecision** jest dołączany do zaznaczenia, a **FlowDecision** nie ma łączników wychodzących, łącznik jest umieszczany w gałęzi **prawdy** .

### <a name="expression-editing"></a>Edytowanie wyrażeń

Domyślnie domyślne skróty klawiaturowe do edycji tekstu Visual Basic są stosowane w edytorze wyrażeń w programie Projektant przepływu pracy z następującymi ograniczeniami:

- Ponowne mapowanie skrótów klawiaturowych dla następujących poleceń nie ma żadnego wpływu. Możesz użyć domyślnych skrótów klawiaturowych, aby uzyskać dostęp do tych poleceń podczas edytowania wyrażenia.

  - Wytnij
  - Kopiuj
  - Wklej
  - Zaznacz wszystko
  - Anulowanie
  - Ponawia

- Aby ponownie zamapować skróty klawiaturowe poleceń edycji wyrażeń wewnątrz Projektant przepływu pracy w programie Visual Studio, Edytuj skróty w zakresie Projektant przepływu pracy. Zmiany wprowadzone w zakresie edytora tekstu nie są automatycznie stosowane do Projektant przepływu pracy. Jeśli chcesz ponownie mapować skróty w obu miejscach, musisz zastosować zmiany dwukrotnie (raz dla każdego zakresu).
