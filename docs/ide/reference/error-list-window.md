---
title: Okno listy błędów
description: Dowiedz się więcej na temat okna Lista błędów i sposobu korzystania z niego do wykonywania zadań związanych z usuwaniem wyświetlanych błędów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Task List
- build errors
- Error List window
- errors [Visual Studio], Error List window
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90d3f8f95cb4b6aef3b2538a26226f5bad40f33b
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112924945"
---
# <a name="error-list-window"></a>Okno listy błędów

> [!NOTE]
> Lista **błędów zawiera** informacje o określonym komunikacie o błędzie. Możesz skopiować numer błędu lub tekst ciągu błędu z **okna Dane** wyjściowe. Aby wyświetlić okno **Dane wyjściowe,** naciśnij **klawisze Ctrl** + **Alt** + **O**. Zobacz [okno Dane wyjściowe](../../ide/reference/output-window.md).

Okno **Lista błędów** umożliwia wykonywanie następujących zadań:

- Wyświetlanie błędów, ostrzeżeń i komunikatów wytwarzanych podczas pisania kodu.

- Znajdź błędy składni zanotowany przez intellisense.

- Znajdowanie błędów wdrażania, niektórych błędów analizy statycznej i błędów wykrytych podczas stosowania zasad szablonów przedsiębiorstwa.

- Kliknij dwukrotnie dowolny wpis komunikatu o błędzie, aby otworzyć plik, w którym występuje problem, i przejdź do lokalizacji błędu.

- Filtruj wyświetlane wpisy i kolumny informacji dla każdego wpisu.

- Wyszukaj określone terminy i zakres wyszukiwania tylko dla bieżącego projektu lub dokumentu.

Aby wyświetlić listę **błędów,** wybierz **pozycję Wyświetl**  >  **listę błędów** lub naciśnij klawisze **Ctrl** + **\\** + **E**.

Możesz wybrać karty **Błędy,** **Ostrzeżenia** i **Komunikaty,** aby wyświetlić różne poziomy informacji.

Aby posortować listę, kliknij dowolny nagłówek kolumny. Aby posortować ponownie według dodatkowej kolumny, przytrzymaj w dół klawisz **Shift** i kliknij kolejny nagłówek kolumny. Aby wybrać, które kolumny są wyświetlane, a które ukryte, wybierz pozycję **Pokaż kolumny** z menu skrótów. Aby zmienić kolejność wyświetlania kolumn, przeciągnij dowolny nagłówek kolumny w lewo lub w prawo.

## <a name="error-list-filters"></a>Filtry listy błędów

Istnieją dwa typy filtrów w dwóch polach rozwijanych: jeden po prawej stronie paska narzędzi i jeden z lewej strony paska narzędzi. Lista rozwijana po lewej stronie paska narzędzi określa zestaw plików kodu do użycia **(całe** **rozwiązanie,** otwieranie dokumentów, bieżący **projekt,** **bieżący dokument).**

Możesz ograniczyć zakres wyszukiwania, aby analizować grupy błędów i działać na nich. Możesz na przykład skupić się na podstawowych błędach, które uniemożliwiają kompilowanie projektu. Dostępne są następujące opcje zakresu:

1. **Otwórz dokumenty:** Pokaż błędy, ostrzeżenia i komunikaty dotyczące otwartych dokumentów.

2. **Bieżący projekt:** wyświetla błędy, ostrzeżenia i komunikaty z projektu  aktualnie wybranego dokumentu w edytorze lub wybranym projekcie w Eksplorator rozwiązań **.**

    > [!NOTE]
    > Filtrowana lista błędów, ostrzeżeń i komunikatów zmieni się, jeśli projekt aktualnie wybranego dokumentu różni się od projektu wybranego w **Eksplorator rozwiązań**.

3. **Bieżący dokument:** wyświetla błędy, ostrzeżenia i komunikaty dla aktualnie wybranego dokumentu w **edytorze** **lub** Eksplorator rozwiązań .

Jeśli filtr jest obecnie stosowany do wyniku wyszukiwania, nazwa filtru jest wyświetlana na pasku tytułu **Lista** błędów. Przyciski **Błędy,**  **Ostrzeżenia** i Komunikaty wyświetlają następnie liczbę wyświetlanych odfiltrowanych elementów wraz z łączną liczbą elementów. Na przykład przyciski pokazują "x of y Errors". Jeśli nie zastosowano filtru, na pasku tytułu jest wyświetlany tylko komunikat "Lista błędów".

Lista po prawej stronie paska narzędzi określa, czy mają być wyświetlane błędy z kompilacji (błędy wynikające z operacji kompilacji), czy z funkcji IntelliSense (błędy wykryte przed uruchomieniem kompilacji), czy z obu tych elementów.

## <a name="search"></a>Wyszukaj

Użyj pola **tekstowego Wyszukaj listę** błędów  po prawej stronie paska narzędzi Lista błędów, aby znaleźć określone błędy na liście błędów. Możesz wyszukać dowolną widoczną kolumnę na liście błędów, a wyniki wyszukiwania są zawsze sortowane na podstawie kolumny, która ma priorytet sortowania, a nie w zastosowanym zapytaniu lub filtrze. Jeśli wybierzesz klawisz **Esc,** gdy fokus znajduje się na liście **błędów,** możesz wyczyścić termin wyszukiwania i przefiltrowane wyniki wyszukiwania. Możesz również kliknąć znak **X** po prawej stronie pola tekstowego, aby go wyczyścić.

## <a name="save"></a>Zapisz

Możesz skopiować listę błędów i zapisać ją w pliku. Wybierz błędy, które chcesz skopiować, a następnie kliknij prawym przyciskiem myszy zaznaczenie, a następnie w menu kontekstowym wybierz pozycję **Kopiuj**. Następnie możesz wkleić błędy do pliku. Jeśli wklejysz błędy do arkusza kalkulacyjnego programu Excel, pola będą wyświetlane jako różne kolumny.

## <a name="ui-element-list"></a>Lista elementów interfejsu użytkownika

Ważność

Wyświetla różne typy wpisów **listy błędów** (**Błąd,** **Komunikat,** **Ostrzeżenie,** **Ostrzeżenie (aktywne)**, **Ostrzeżenie (nieaktywne)**.

Kod

Wyświetla kod błędu.

Opis

Wyświetla tekst wpisu.

Project

Wyświetla nazwę bieżącego projektu.

Plik

Wyświetla nazwę pliku.

Linia

Wyświetla wiersz, w którym występuje problem.
