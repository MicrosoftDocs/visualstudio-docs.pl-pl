---
title: Okno Lista błędów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ErrorList
helpviewer_keywords:
- Task List
- build errors
- Error List window
- errors [Visual Studio], Error List window
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 35be5ddeedf0b081fa94e399f294151e73a157ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657732"
---
# <a name="error-list-window"></a>Okno listy błędów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

KORYGUJĄC
> Lista błędów wyświetla informacje o określonym komunikacie o błędzie. Możesz skopiować numer błędu lub tekst ciągu błędu z okna danych wyjściowych. Aby wyświetlić okno dane wyjściowe, naciśnij kombinację klawiszy Ctrl + Alt + O. Zobacz [okno dane wyjściowe](../../ide/reference/output-window.md).

 Aplikacje można opracowywać szybciej przy użyciu okna **Lista błędów** . Na przykład można wykonać następujące zadania:

- Wyświetlanie błędów, ostrzeżeń i komunikatów generowanych podczas pisania kodu.

- Znajdź błędy składniowe zanotowane przez funkcję IntelliSense.

- Znajdź błędy wdrażania, niektóre błędy analizy statycznej i błędy wykryte podczas stosowania zasad szablonów przedsiębiorstwa.

- Kliknij dwukrotnie dowolny wpis komunikatu o błędzie, aby otworzyć plik, w którym wystąpił problem, i przejdź do lokalizacji błędu.

- Filtruj, które wpisy są wyświetlane, a kolumny informacji są wyświetlane dla każdego wpisu.

- Wyszukaj określone terminy i zakres wyszukiwania tylko dla bieżącego projektu lub dokumentu.

  Aby wyświetlić **Lista błędów**, kliknij przycisk **Wyświetl/Lista błędów**lub **Ctrl + \\ + E**.

  Możesz wybrać karty **Błędy**, **ostrzeżenia**i **komunikaty** , aby zobaczyć różne poziomy informacji.

  Aby posortować listę, kliknij dowolny nagłówek kolumny. Aby posortować ponownie według dodatkowej kolumny, przytrzymaj wciśnięty klawisz SHIFT i kliknij inny nagłówek kolumny. Aby wybrać kolumny, które są wyświetlane, a które są ukryte, wybierz polecenie **Pokaż kolumny** z menu skrótów. Aby zmienić kolejność wyświetlania kolumn, przeciągnij dowolny nagłówek kolumny w lewo lub w prawo.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od opisanych tutaj, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, kliknij przycisk **Narzędzia/Importuj i Eksportuj ustawienia**. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="error-list-filters"></a>Filtry Lista błędów
 Istnieją dwa typy filtrów w dwóch polach rozwijanych, jeden po prawej stronie paska narzędzi i jeden z lewej strony paska narzędzi. Lista rozwijana po lewej stronie paska narzędzi określa zestaw plików kodu do użycia (**całe rozwiązanie**, **otwarte dokumenty**, **bieżący projekt**, **bieżący dokument**).

 Możesz ograniczyć zakres wyszukiwania do analizowania i działania w grupach błędów. Na przykład możesz chcieć skupić się na podstawowych błędach, które uniemożliwiają Kompilowanie projektu. Opcje zakresu obejmują:

1. **Otwarte dokumenty**: Pokaż błędy, ostrzeżenia i komunikaty dla otwartych dokumentów.

2. **Bieżący projekt**: Pokaż błędy, ostrzeżenia i komunikaty z projektu aktualnie wybranego dokumentu w **Edytorze** lub w wybranym projekcie w **Eksplorator rozwiązań**.

   > [!NOTE]
   > Filtrowana lista błędów, ostrzeżeń i komunikatów ulegnie zmianie, jeśli projekt aktualnie wybranego dokumentu różni się od projektu wybranego w **Eksplorator rozwiązań**.

3. **Bieżący dokument**: Pokaż błędy, ostrzeżenia i komunikaty dla aktualnie wybranego dokumentu w **Edytorze** lub **Eksplorator rozwiązań**.

   Jeśli filtr jest aktualnie stosowany do wyniku wyszukiwania, nazwa filtru pojawia się na pasku tytułu **Lista błędów** . Przyciski **Błędy**, **ostrzeżenia**i **komunikaty** wyświetlają liczbę elementów filtrowanych, które są wyświetlane wraz z łączną liczbą elementów; na przykład przyciski zawierają błędy x z y. Jeśli żaden filtr nie zostanie zastosowany, na pasku tytułu jest wyświetlany tylko komunikat "Lista błędów".

   Lista po prawej stronie paska narzędzi określa, czy mają być wyświetlane błędy kompilacji (błędy spowodowane operacją kompilacji), czy z funkcji IntelliSense (błędy wykryte przed uruchomieniem kompilacji) lub z obu tych elementów.

## <a name="search"></a>Wyszukiwanie
 Użyj pola tekstowego **szukaj Lista błędów** po prawej stronie **Lista błędów** pasku narzędzi, aby znaleźć konkretne błędy na liście błędów. Możesz wyszukać dowolną widoczną kolumnę na liście błędów, a wyniki wyszukiwania są zawsze sortowane na podstawie kolumny, która ma priorytet sortowania zamiast zapytania lub zastosowany filtr. Jeśli wybierzesz klawisz **ESC** , gdy fokus znajduje się w **Lista błędów**, możesz wyczyścić wyszukiwany termin i wyniki wyszukiwania odfiltrowanego. Możesz również kliknąć **symbol X** po prawej stronie pola tekstowego, aby usunąć jego zaznaczenie.

## <a name="save"></a>Zapisz
 Można skopiować listę błędów i zapisać ją w pliku. Wybierz błędy, które chcesz skopiować, a następnie kliknij prawym przyciskiem myszy zaznaczenie, a następnie w menu kontekstowym wybierz polecenie **Kopiuj**. Można następnie wkleić błędy do pliku. W przypadku wklejenia błędów do arkusza kalkulacyjnego programu Excel pola są wyświetlane jako różne kolumny.

## <a name="ui-element-list"></a>Lista elementów interfejsu użytkownika
 Ważność wyświetla różne typy wpisów **Lista błędów** (**błąd**, **komunikat**, **Ostrzeżenie**, **ostrzeżenie (aktywne)**, **ostrzeżenie (nieaktywne)**.

 Kod wyświetla kod błędu.

 Opis wyświetla tekst wpisu.

 Projekt wyświetla nazwę bieżącego projektu.

 Plik wyświetla nazwę pliku.

 Wiersz wyświetla wiersz, w którym występuje problem.
