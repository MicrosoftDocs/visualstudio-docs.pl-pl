---
title: Zastąp w plikach | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- Find and Replace window, Replace in Files tab
- Replace in Files tab, Find and Replace window
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 001f1faa969275788b10bc9bd1e6398373a54b37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669973"
---
# <a name="replace-in-files"></a>Zastąp w plikach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zastąp w plikach * * umożliwia przeszukanie kodu określonego zestawu plików dla ciągu lub wyrażenia, a także zmianę niektórych lub wszystkich znalezionych dopasowań. Znalezione dopasowania i wykonane akcje są wymienione w oknie **Znajdź wyniki** wybrane w obszarze **Opcje wyników**.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Możesz użyć dowolnej z poniższych metod, aby wyświetlić **Zamień w plikach** w oknie **Znajdź i Zamień** .

### <a name="to-display-replace-in-files"></a>Aby wyświetlić Zamień w plikach

1. W menu **Edycja** rozwiń pozycję **Znajdź i Zamień**.

2. Wybierz **Zamień w plikach**.

     oraz

     Jeśli okno **Znajdź i Zamień** jest już otwarte, na pasku narzędzi wybierz opcję **Zamień w plikach**.

## <a name="find-what"></a>Znajdź
 Aby wyszukać nowy ciąg tekstowy lub wyrażenie, określ je w polu. Aby wyszukać dowolny z 20 ostatnio wyszukiwanych ciągów, Otwórz listę i wybierz ciąg, dla którego chcesz wyszukać. Wybierz przycisk sąsiadujący **Konstruktor wyrażeń** , jeśli chcesz użyć co najmniej jednego wyrażenia regularnego w ciągu wyszukiwania. Aby uzyskać więcej informacji, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="replace-with"></a>Zamień na
 Aby zamienić wystąpienia ciągu w polu **Znajdź** z innym ciągiem, wprowadź ciąg zamienny w polu **Zamień na** . Aby usunąć wystąpienia ciągu w polu **Znajdź** , pozostaw to pole puste. Otwórz listę, aby wyświetlić 20 ciągów, dla których Przeszukiwano ostatnio. Wybierz przycisk sąsiadujący **Konstruktor wyrażeń** , jeśli chcesz użyć co najmniej jednego wyrażenia regularnego w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Szukaj w
 Opcja wybrana z listy rozwijanej **Szukaj w** określa, czy **Zastąp w plikach** wyszukiwanie tylko w aktualnie aktywnych plikach, czy wyszukiwanie wszystkich plików przechowywanych w określonych folderach. Wybierz z listy zakres wyszukiwania, wpisz ścieżkę folderu, lub kliknij przycisk **Przeglądaj (...)** , aby wyświetlić okno dialogowe **Wybieranie folderów wyszukiwania** i wybrać zestaw folderów do przeszukania. Możesz również wpisać ścieżkę bezpośrednio do pola **Szukaj w** .

> [!NOTE]
> Jeśli wybrana opcja **Szukaj w** powoduje wyszukanie pliku, który został wyewidencjonowany z kontroli kodu źródłowego, przeszukiwany jest tylko wersja tego pliku, która została pobrana na komputer lokalny.

## <a name="find-options"></a>Opcje znajdowania
 Można rozwinąć lub zwinąć sekcję **Znajdź opcje** . Można wybrać lub wyczyścić następujące opcje:

 Uwzględnij wielkość liter po zaznaczeniu, w oknach **Znajdź wyniki** są wyświetlane tylko wystąpienia elementu **Find** , które są dopasowane do zawartości i według wielkości liter. Na przykład wyszukiwanie "MyObject" z wybraną **wielkością liter** zwróci wartość "MyObject", ale nie "MyObject" lub "MyObject".

 Dopasowuje całe słowo, gdy jest zaznaczone, okna **Znajdź wyniki** będą wyświetlały tylko wystąpienia słowa **Find** , które są dopasowane w kompletnych wyrazach. Na przykład wyszukiwanie "MyObject" zwróci wartość "MyObject", ale nie "CMyObject" lub "MyObjectC".

 Używaj wyrażeń regularnych, gdy to pole wyboru jest zaznaczone, można użyć notacji specjalnych do definiowania wzorców tekstu w polach tekstowych **Znajdź** lub **Zamień na** . Aby zapoznać się z listą tych notacji, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Sprawdź te typy plików ta lista wskazuje typy plików do przeszukania **w katalogach wyszukiwania.** Jeśli to pole pozostanie puste, zostaną przeszukane wszystkie pliki znajdujące się w katalogach **wyszukiwania** .

 Wybierz dowolny element na liście, aby wprowadzić wstępnie skonfigurowany ciąg wyszukiwania, który będzie znajdował pliki tych konkretnych typów.

## <a name="result-options"></a>Opcje wyników
 Można rozwinąć lub zwinąć sekcję **Opcje wyniku** . Można wybrać lub wyczyścić następujące opcje:

 Okno wyników wyszukiwania 1 po zaznaczeniu, wyniki bieżącego wyszukiwania zastąpią zawartość okna **Wyszukiwanie wyników 1** . To okno zostanie automatycznie otwarte w celu wyświetlenia wyników wyszukiwania. Aby otworzyć to okno ręcznie, wybierz pozycję **inne okna** w menu **Widok** i wybierz pozycję **Znajdź wyniki 1**.

 Okno wyników wyszukiwania 2 po zaznaczeniu, wyniki bieżącego wyszukiwania zastąpią zawartość okna **Wyszukiwanie wyników 2** . To okno zostanie automatycznie otwarte w celu wyświetlenia wyników wyszukiwania. Aby otworzyć to okno ręcznie, wybierz pozycję **inne okna** w menu **Widok** i wybierz pozycję **Znajdź wyniki 2**.

 Wyświetlaj nazwy plików tylko wtedy, gdy to pole wyboru jest zaznaczone, Okna Znajdź wyniki wyświetlają pełne nazwy i ścieżki dla wszystkich plików, które zawierają ciąg wyszukiwania. Jednak wyniki nie uwzględniają wiersza kodu, w którym pojawia się ciąg. To pole wyboru jest dostępne tylko do znajdowania w plikach.

 Po wybraniu tej operacji pozostaw zmodyfikowane pliki otwarte po zaimportowaniu wszystkich, pozostawiając otwarte wszystkie pliki, w których zostały wykonane zamiany, aby można było cofnąć lub zapisać zmiany. Ograniczenia pamięci mogą ograniczyć liczbę plików, które mogą pozostać otwarte po operacji Zamień.

> [!CAUTION]
> Można użyć **Cofnij** tylko dla plików, które pozostaną otwarte do edycji. Jeśli ta opcja nie zostanie wybrana, pliki, które nie zostały jeszcze otwarte do edycji, pozostaną zamknięte i w tych plikach nie będzie dostępna opcja **Cofnij** .

## <a name="see-also"></a>Zobacz też
 [Znajdowanie i zamienianie tekstu](../ide/finding-and-replacing-text.md) [Znajdź w plikach](../ide/find-in-files.md) [polecenia programu Visual Studio](../ide/reference/visual-studio-commands.md)
