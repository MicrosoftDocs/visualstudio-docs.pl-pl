---
title: Znajdź w plikach
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e1f067df647f843819e085f283005606699f3bb
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595478"
---
# <a name="find-in-files"></a>Znajdź w plikach

**Znajdź w plikach** umożliwia wyszukiwanie określonego zestawu plików. Liczba znalezionych dopasowań i akcje wykonywane są wymienione w **Find Results** wybranego w oknie **wyniku opcje**.

Możesz użyć dowolnej z poniższych metod, aby wyświetlić **Znajdź w plikach** w oknie **Znajdź i Zamień** .

## <a name="to-display-find-in-files"></a>Aby wyświetlić Znajdź w plikach

1. Na pasku menu wybierz **edytuj** > **Znajdź i Zamień**.

1. Wybierz pozycję **Znajdź w plikach**.

Aby anulować operację wyszukiwania, naciśnij klawisz **Ctrl** + **Break**.

> [!NOTE]
> Narzędzie Znajdź i Zamień nie przeszukuje katalogów z atrybutem `Hidden` lub `System`.

## <a name="find-what"></a>Znajdź

Aby wyszukać nowy ciąg tekstowy lub wyrażenie, należy je określić w polu. Aby wyszukać dowolne z 20 ciągów, które wyszukiwane ostatnio, Otwieranie listy rozwijanej, a następnie wybierz ciągu. Wybierz sąsiadujących **Konstruktor wyrażeń** przycisk, jeśli chcesz użyć co najmniej jednego wyrażenia regularne w wyszukiwanym ciągu. Aby uzyskać więcej informacji, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> **Konstruktor wyrażeń** przycisk zostanie włączona tylko, jeśli wybrano **Użyj wyrażeń regularnych** w obszarze **opcje szukania**.

## <a name="look-in"></a>Szukaj w

Opcja wybrana z listy rozwijanej **Szukaj w** określa, czy **Wyszukiwanie w plikach** przeszukuje tylko w aktualnie aktywnych plikach, czy we wszystkich plikach przechowywanych w określonych folderach. Wybierz zakres wyszukiwania z listy lub kliknij przycisk **Przeglądaj (...)** , aby wyświetlić okno dialogowe **Wybieranie folderów wyszukiwania** i wprowadzić własny zestaw katalogów. Możesz również wpisać ścieżkę bezpośrednio do **przeszukania** pole.

> [!WARNING]
> W przypadku **wszystkich rozwiązań** lub **bieżących opcji projektu** pliki projektu i rozwiązania nie są przeszukiwane. Jeśli chcesz wyszukać w plikach projektu, wybierz folder wyszukiwania.

> [!NOTE]
> Jeśli **przeszukania** wybrana opcja powoduje, że użytkownik może wyszukiwać pliku, który został wyewidencjonowany z kontrolą kodu źródłowego, przeszukiwany jest tylko wersja tego pliku, który został pobrany na komputer lokalny.

## <a name="include-subfolders"></a>Uwzględnij podfoldery

Określa, że będą przeszukiwane podfoldery **Szukaj w** folderze.

## <a name="find-options"></a>Opcje znajdowania

Można rozwinąć lub zwinąć **opcje szukania** sekcji. Następujące opcje można zaznaczyć lub wyczyścić:

**Uwzględnij wielkość liter**

Po wybraniu wyszukiwanie **wyników** wyszukiwania będzie uwzględniać wielkość liter

**Uwzględnij całe wyrazy**

Po zaznaczeniu okna **Znajdź wyniki** będą zwracać tylko dopasowania do całego wyrazu.

**Używanie wyrażeń regularnych**

Jeśli to pole wyboru jest zaznaczone, można użyć notacji specjalnych do definiowania wzorców tekstu do dopasowania w polach tekstowych **Znajdź** lub **Zamień** na. Aby zapoznać się z listą tych notacji, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Spójrz na następujące typy plików**

Ta lista wskazuje typy plików, aby wyszukiwać w **przeszukania** katalogów. Jeśli to pole jest puste, zostaną przeszukane wszystkie pliki znajdujące się w katalogach **wyszukiwania** .

Wybierz dowolny element na liście, aby wprowadzić wstępnie wyszukiwany ciąg, który zawiera pliki określonego typu.

## <a name="result-options"></a>Opcje wyników

Można rozwinąć lub zwinąć **wyniku opcje** sekcji. Następujące opcje można zaznaczyć lub wyczyścić:

**Okno wyników wyszukiwania 1**

Po wybraniu wyniki bieżące wyszukiwanie spowoduje zastąpienie zawartości **Znajdź wyniki 1** okna. To okno zostanie otwarty automatycznie do wyświetlenia wyników wyszukiwania. Aby ręcznie otworzyć to okno, wybierz **Windows inne** z **widoku** menu i wybierz polecenie **Znajdź wyniki 1**.

**Okno wyników wyszukiwania 2**

Po wybraniu wyniki bieżące wyszukiwanie spowoduje zastąpienie zawartości **Znajdź wyniki 2** okna. To okno zostanie otwarty automatycznie do wyświetlenia wyników wyszukiwania. Aby ręcznie otworzyć to okno, wybierz **Windows inne** z **widoku** menu i wybierz polecenie **Znajdź wyniki 2**.

**Wyświetl tylko nazwy pliku**

Wyświetla listę plików zawierających dopasowania wyszukiwania zamiast wyświetlania wyszukiwania pasuje do samego siebie.

**Dołącz wyniki**

Dołącza wyniki wyszukiwania do poprzednich wyników wyszukiwania.

## <a name="see-also"></a>Zobacz także

- [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)
- [Zastąp w plikach](../ide/replace-in-files.md)
- [Polecenia programu Visual Studio](../ide/reference/visual-studio-commands.md)
