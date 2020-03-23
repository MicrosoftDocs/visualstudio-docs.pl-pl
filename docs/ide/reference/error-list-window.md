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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c6d925f61714c524f97a57690870229b2340d21
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569666"
---
# <a name="error-list-window"></a>Okno listy błędów

> [!NOTE]
> **Na liście błędów** są wyświetlane informacje o określonym komunikacie o błędzie. Numer błędu lub tekst ciągu błędu można skopiować z okna **Dane wyjściowe.** Aby wyświetlić okno **Wyjście,** naciśnij **klawisze Ctrl**+**Alt**+**O**. Zobacz [Okno Wyjście](../../ide/reference/output-window.md).

Okno **Lista błędów** umożliwia wykonywanie następujących zadań:

- Wyświetla błędy, ostrzeżenia i komunikaty generowane podczas pisania kodu.

- Znajdź błędy składni odnotowane przez IntelliSense.

- Znajdź błędy wdrażania, niektóre błędy analizy statycznej i błędy wykryte podczas stosowania zasad szablonu przedsiębiorstwa.

- Kliknij dwukrotnie dowolny wpis komunikatu o błędzie, aby otworzyć plik, w którym występuje problem, i przenieść do lokalizacji błędu.

- Filtruj, które wpisy są wyświetlane i które kolumny informacji są wyświetlane dla każdego wpisu.

- Wyszukaj określone terminy i zakres wyszukiwania tylko do bieżącego projektu lub dokumentu.

Aby wyświetlić **listę błędów,** wybierz pozycję **Wyświetl** > **listę błędów**lub naciśnij klawisz **Ctrl**+**\\**+**E**.

Można wybrać karty **Błędy,** **Ostrzeżenia**i **Wiadomości,** aby wyświetlić różne poziomy informacji.

Aby posortować listę, kliknij dowolny nagłówek kolumny. Aby posortować ponownie według dodatkowej kolumny, przytrzymaj klawisz **Shift** i kliknij inny nagłówek kolumny. Aby wybrać kolumny, które są wyświetlane, a które są ukryte, wybierz polecenie Pokaż kolumny z menu **skrótów.** Aby zmienić kolejność wyświetlania kolumn, przeciągnij dowolny nagłówek kolumny w lewo lub w prawo.

## <a name="error-list-filters"></a>Filtry listy błędów

Istnieją dwa typy filtrów w dwóch polach rozwijanych, jeden po prawej stronie paska narzędzi i jeden po lewej stronie paska narzędzi. Lista rozwijana po lewej stronie paska narzędzi określa zestaw plików kodu do użycia (**Całe rozwiązanie**, **Otwarte dokumenty, Bieżący** **projekt,** **Bieżący dokument**).

Można ograniczyć zakres wyszukiwania do analizowania i działania na grupy błędów. Na przykład można skupić się na podstawowych błędów, które uniemożliwiają kompilacji projektu. Opcje określania zakresu obejmują:

1. **Otwórz dokumenty:** Pokaż błędy, ostrzeżenia i komunikaty dla otwartych dokumentów.

2. **Bieżący projekt**: Pokaż błędy, ostrzeżenia i komunikaty z projektu aktualnie wybranego dokumentu w **edytorze** lub wybranego projektu w **Eksploratorze rozwiązań**.

    > [!NOTE]
    > Filtrowana lista błędów, ostrzeżeń i komunikatów ulegnie zmianie, jeśli projekt aktualnie wybranego dokumentu różni się od projektu wybranego w **Eksploratorze rozwiązań**.

3. **Bieżący dokument**: Pokaż błędy, ostrzeżenia i komunikaty dla aktualnie wybranego dokumentu w **Edytorze** lub **Eksploratorze rozwiązań**.

Jeśli filtr jest obecnie stosowany do wyniku wyszukiwania, nazwa filtru pojawia się na pasku tytułu **listy błędów.** Przyciski **Błędy,** **Ostrzeżenia**i **Wiadomości** wyświetlają następnie liczbę wyświetlanych filtrowanych elementów wraz z całkowitą liczbą elementów. Na przykład przyciski pokazują "x y Błędy". Jeśli filtr nie zostanie zastosowany, na pasku tytułu jest dostępna tylko "Lista błędów".

Lista po prawej stronie paska narzędzi określa, czy mają być wyświetlane błędy z kompilacji (błędy wynikające z operacji kompilacji) lub z intellisense (błędy wykryte przed uruchomieniem kompilacji), czy z obu.

## <a name="search"></a>Wyszukiwanie

Użyj pola tekstowego **Lista błędów wyszukiwania** po prawej stronie paska narzędzi **Lista błędów,** aby znaleźć określone błędy na liście błędów. Możesz wyszukiwać w dowolnej widocznej kolumnie na liście błędów, a wyniki wyszukiwania są zawsze sortowane na podstawie kolumny o priorytecie, a nie na kwerendzie lub zastosowanej filtrze. Jeśli wybierzesz klawisz **Esc,** gdy fokus znajduje się na **liście błędów,** możesz wyczyścić wyszukiwany termin i przefiltrowane wyniki wyszukiwania. Możesz również kliknąć **znak X** po prawej stronie pola tekstowego, aby go wyczyścić.

## <a name="save"></a>Zapisz

Listę błędów można skopiować i zapisać w pliku. Zaznacz błędy, które chcesz skopiować, a następnie kliknij prawym przyciskiem myszy zaznaczenie, a następnie w menu kontekstowym wybierz polecenie **Kopiuj**. Następnie można wkleić błędy do pliku. Jeśli błędy zostanie wklejone do arkusza kalkulacyjnego programu Excel, pola będą wyświetlane jako różne kolumny.

## <a name="ui-element-list"></a>Lista elementów interfejsu użytkownika

Ważność

Wyświetla różne typy wpisu **listy błędów** (**Błąd**, **Komunikat**, **Ostrzeżenie**, **Ostrzeżenie (aktywny)**, **Ostrzeżenie (nieaktywne)**.

Code

Wyświetla kod błędu.

Opis

Wyświetla tekst wpisu.

Project

Wyświetla nazwę bieżącego projektu.

Plik

Wyświetla nazwę pliku.

Wiersz

Wyświetla linię, w której występuje problem.
