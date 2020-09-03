---
title: Znajdź w plikach | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.findinfiles
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
ms.assetid: 989e0737-46d7-4474-8453-fad52a74669d
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5e21d0880813452e37c9e20afdc98321e4b2e3a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655900"
---
# <a name="find-in-files"></a>Znajdź w plikach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Znajdź w plikach * * umożliwia wyszukiwanie określonego zestawu plików. Znalezione dopasowania i wykonane akcje są wymienione w oknie **Znajdź wyniki** wybrane w obszarze **Opcje wyników**.

 Możesz użyć dowolnej z poniższych metod, aby wyświetlić **Znajdź w plikach** w oknie **Znajdź i Zamień** .

### <a name="to-display-find-in-files"></a>Aby wyświetlić Znajdź w plikach

1. Na pasku menu wybierz **Edytuj**, **Znajdź i Zamień**.

2. Wybierz pozycję **Znajdź w plikach**.

   Aby anulować operację wyszukiwania, naciśnij klawisze CTRL + BREAK.

> [!NOTE]
> Narzędzie Znajdź i Zamień nie przeszukuje katalogów z `Hidden` `System` ustawionym atrybutem lub.

## <a name="find-what"></a>Znajdź
 Aby wyszukać nowy ciąg tekstowy lub wyrażenie, określ je w polu. Aby wyszukać dowolny z 20 ostatnio wyszukiwanych ciągów, Otwórz listę i wybierz ciąg, dla którego chcesz wyszukać. Wybierz przycisk sąsiadujący **Konstruktor wyrażeń** , jeśli chcesz użyć co najmniej jednego wyrażenia regularnego w ciągu wyszukiwania. Aby uzyskać więcej informacji, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Szukaj w
 Opcja wybrana z listy rozwijanej **Szukaj w** określa, czy **Wyszukiwanie w plikach** przeszukuje tylko w aktualnie aktywnych plikach, czy we wszystkich plikach przechowywanych w określonych folderach. Wybierz zakres wyszukiwania z listy lub kliknij przycisk **Przeglądaj (...)** , aby wyświetlić okno dialogowe **Wybieranie folderów wyszukiwania** i wprowadzić własny zestaw katalogów. Możesz również wpisać ścieżkę bezpośrednio do pola **Szukaj w** .

> [!WARNING]
> W przypadku **wszystkich rozwiązań** lub **bieżących opcji projektu** pliki projektu i rozwiązania nie są przeszukiwane. Jeśli chcesz wyszukać w plikach projektu, wybierz folder wyszukiwania.

> [!NOTE]
> Jeśli wybrana opcja **Szukaj w** powoduje wyszukanie pliku, który został wyewidencjonowany z kontroli kodu źródłowego, przeszukiwany jest tylko wersja tego pliku, która została pobrana na komputer lokalny.

## <a name="include-subfolders"></a>Uwzględnij podfoldery
 Określa, że będą przeszukiwane podfoldery **Szukaj w** folderze.

## <a name="find-options"></a>Opcje znajdowania
 Można rozwinąć lub zwinąć sekcję **Znajdź opcje** . Można wybrać lub wyczyścić następujące opcje:

 Uwzględnij wielkość liter po zaznaczeniu, wyszukiwanie **wyników** wyszukiwania będzie uwzględniać wielkość liter

 Dopasowuje całe słowo, gdy jest zaznaczone, okna **Znajdź wyniki** będą zwracać tylko dopasowania do całego wyrazu.

 Używaj wyrażeń regularnych, jeśli to pole wyboru jest zaznaczone, można użyć notacji specjalnych do definiowania wzorców tekstu do dopasowania w polach tekstowych **Znajdź** i **Zamień** . Aby zapoznać się z listą tych notacji, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Sprawdź te typy plików ta lista wskazuje typy plików do przeszukania **w katalogach wyszukiwania.** Jeśli to pole jest puste, zostaną przeszukane wszystkie pliki znajdujące się w katalogach **wyszukiwania** .

 Wybierz dowolny element na liście, aby wprowadzić wstępnie skonfigurowany ciąg wyszukiwania, który będzie znajdował pliki tych konkretnych typów.

## <a name="result-options"></a>Opcje wyników
 Można rozwinąć lub zwinąć sekcję **Opcje wyniku** . Można wybrać lub wyczyścić następujące opcje:

 Okno wyników wyszukiwania 1 po zaznaczeniu, wyniki bieżącego wyszukiwania zastąpią zawartość okna **Wyszukiwanie wyników 1** . To okno zostanie automatycznie otwarte w celu wyświetlenia wyników wyszukiwania. Aby otworzyć to okno ręcznie, wybierz pozycję **inne okna** w menu **Widok** i wybierz pozycję **Znajdź wyniki 1**.

 Okno wyników wyszukiwania 2 po zaznaczeniu, wyniki bieżącego wyszukiwania zastąpią zawartość okna **Wyszukiwanie wyników 2** . To okno zostanie automatycznie otwarte w celu wyświetlenia wyników wyszukiwania. Aby otworzyć to okno ręcznie, wybierz pozycję **inne okna** w menu **Widok** i wybierz pozycję **Znajdź wyniki 2**.

 Wyświetlaj nazwy plików wyświetla tylko listę plików zawierających dopasowania wyszukiwania zamiast wyświetlania wyszukiwania pasuje do samego siebie.

 Dołącz wyniki dołącza wyniki wyszukiwania do poprzednich wyników wyszukiwania.

## <a name="see-also"></a>Zobacz też
 [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md) [Zamień w plikach](../ide/replace-in-files.md) [polecenia programu Visual Studio](../ide/reference/visual-studio-commands.md)
