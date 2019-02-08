---
title: Okno listy błędów
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ErrorList
helpviewer_keywords:
- Task List
- build errors
- Error List window
- errors [Visual Studio], Error List window
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fe70a8c7daeac86ea3a354f81d8462ca7f4e451
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55933980"
---
# <a name="error-list-window"></a>Okno listy błędów

> [!NOTE]
> **Lista błędów** przedstawia informacje na temat konkretnego komunikatu o błędzie. Możesz skopiować numer błędu lub ciąg tekstu błędu błędu z **dane wyjściowe** okna. Aby wyświetlić **dane wyjściowe** naciśnij klawisze **Ctrl**+**Alt**+**O**. Zobacz [okno danych wyjściowych](../../ide/reference/output-window.md).

**Lista błędów** okno umożliwia wykonywanie następujących zadań:

-   Wyświetl błędy, ostrzeżenia i komunikaty generowane podczas pisania kodu.

-   Znajdź błędy składniowe oznaczone przez technologię IntelliSense.

-   Znajdź błędy wdrażania, niektóre analizy statycznej błędy i błędy wykryte podczas stosowania zasad szablonu organizacji.

-   Kliknij dwukrotnie wpis komunikatu o błędzie, wszelkie można otworzyć pliku, gdzie występuje problem i przejść do lokalizacji błędu.

-   Filtruj, które wpisy są wyświetlane i które kolumny informacji są wyświetlane dla każdego wpisu.

-   Wyszukaj konkretne terminy i Ogranicz zakres wyszukiwania do tylko bieżącego projektu lub dokumentu.

Aby wyświetlić **lista błędów**, wybierz **widoku** > **lista błędów**, lub naciśnij **Ctrl** + **\\** + **E**.

Możesz wybrać **błędy**, **ostrzeżenia**, i **wiadomości** kart, aby wyświetlić różne poziomy informacji.

Aby posortować listę, kliknij nagłówek dowolnej kolumny. Aby ponownie sortować według dodatkowej kolumny, przytrzymaj wciśnięty **Shift** klucza i kliknij inny nagłówek kolumny. Aby wybrać kolumny, które są wyświetlane, a które ukryte, wybierz **Pokaż kolumny** z menu skrótów. Aby zmienić kolejność wyświetlania kolumn, przeciągnij dowolny nagłówek kolumny w lewo lub w prawo.

## <a name="error-list-filters"></a>Filtry listy błędów

Istnieją dwa rodzaje filtru w dwa pola listy rozwijanej: jeden po prawej stronie paska narzędzi, a drugi z lewej strony paska narzędzi. Lista rozwijana na pasku narzędzi po lewej stronie określa zestaw plików kodu do użycia (**całe rozwiązanie**, **otwarte dokumenty**, **bieżący projekt**,  **Bieżący dokument**).

Możesz ograniczyć zakres wyszukiwania do analizowania i działają na grupy błędów. Na przykład można skoncentrować się na podstawowych błędach, które uniemożliwiają kompilowania projektu. Opcje zakresu są następujące:

1.  **Otwieranie dokumentów**: Pokaż błędy, ostrzeżenia i komunikaty dla otwartych dokumentów.

2.  **Bieżący projekt**: Pokaż błędy, ostrzeżenia i komunikaty z projektu aktualnie wybranego dokumentu w **edytora** lub wybranego projektu w **Eksploratora rozwiązań**.

    > [!NOTE]
    > Filtrowana lista błędy, ostrzeżenia i komunikaty ulegnie zmianie, jeśli projekt aktualnie wybranego dokumentu różni się od projektu wybranego w **Eksploratora rozwiązań**.

3.  **Bieżący dokument**: Pokaż błędy, ostrzeżenia i komunikaty dla aktualnie wybranego dokumentu w **edytora** lub **Eksploratora rozwiązań**.

Jeśli filtr jest obecnie stosowany do wyników wyszukiwania, nazwę filtra pojawia się w **lista błędów** paska tytułu. **Błędy**, **ostrzeżenia**, i **wiadomości** przyciski, a następnie wyświetla liczbę odfiltrowane elementy są wyświetlane wraz z całkowitą liczbę elementów. Na przykład przyciski Pokaż "x z y błędów". Jeśli żaden filtr zostanie zastosowany, na pasku tytułu widać tylko "Lista błędów".

Listy po prawej stronie paska narzędzi, określa, czy błędy kompilacji (błędy wynikające z operacji kompilacji) lub z funkcji IntelliSense (błędy wykryte przed uruchomieniem kompilacji) lub obu.

## <a name="search"></a>Wyszukaj

Użyj **lista wyszukiwania błędów** pola tekstowego po prawej stronie **lista błędów** narzędzi, aby znaleźć określone błędy na liście błędów. Możesz wyszukiwać według dowolnej widocznej kolumny na liście błędów, a wyniki wyszukiwania są zawsze sortowane w oparciu o kolumnę, która ma priorytet sortowania, a nie o kwerendę lub zastosowany filtr. Jeśli wybierzesz **Esc** klucza, gdy fokus jest ustawiony w **lista błędów**, może to wyczyszczenie wyszukiwanego terminu i przefiltrowanych wyników wyszukiwania. Możesz również kliknąć **X** po prawej stronie pola tekstowego, aby je wyczyścić.

## <a name="save"></a>Zapisanie

Możesz skopiować listę błędów i zapisz go w pliku. Zaznacz błędy, aby skopiować i kliknij prawym przyciskiem myszy zaznaczenie, a następnie w menu kontekstowym wybierz **kopiowania**. Możesz następnie wkleić błędy do pliku. Jeśli wklejasz błędy do arkusza kalkulacyjnego programu Excel, pola są wyświetlane jako różne kolumny.

## <a name="ui-element-list"></a>Lista elementów interfejsu użytkownika

Ważność

Wyświetla różne rodzaje **lista błędów** wejścia (**błąd**, **komunikat**, **ostrzeżenie**, **ostrzeżenie (aktywne)**, **Ostrzeżenie (nieaktywne)**.

Kod

Wyświetla kod błędu.

Opis

Wyświetla tekst wpisu.

Projekt

Wyświetla nazwę bieżącego projektu.

Plik

Wyświetla nazwę pliku.

Wiersz

Wyświetla wiersz, w którym występuje problem.