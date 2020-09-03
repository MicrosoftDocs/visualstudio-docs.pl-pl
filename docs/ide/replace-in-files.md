---
title: Znajdź i Zamień w plikach
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- find and replace
- replace in files
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dddd55714e53516ba1ccd8a11c99761a4db7136a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75585629"
---
# <a name="replace-in-files"></a>Zastąp w plikach

Polecenie **Zamień w plikach** umożliwia przeszukanie kodu określonego zestawu plików dla ciągu lub wyrażenia, a także zmianę niektórych lub wszystkich znalezionych dopasowań. Znalezione dopasowania i wykonane akcje są wymienione w oknie **Znajdź wyniki** wybrane w obszarze **Opcje wyników**.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w **pomocy** , w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, na przykład **Ogólne** lub **Visual C++** ustawienia, wybierz pozycję **Narzędzia**  >  **Importuj i Eksportuj ustawienia**, a następnie wybierz pozycję **Zresetuj wszystkie ustawienia**.

Możesz użyć dowolnej z poniższych metod, aby wyświetlić **Zamień w plikach** w oknie **Znajdź i Zamień** .

## <a name="to-display-replace-in-files"></a>Aby wyświetlić Zamień w plikach

1. W menu **Edycja** rozwiń pozycję **Znajdź i Zamień**.

2. Wybierz **Zamień w plikach**.

   oraz

   Jeśli okno **Znajdź i Zamień** jest już otwarte, na pasku narzędzi wybierz opcję **Zamień w plikach**.

## <a name="find-what"></a>Znajdź

Aby wyszukać nowy ciąg tekstowy lub wyrażenie, określ je w polu. Aby wyszukać dowolny z 20 ostatnio wyszukiwanych ciągów, Otwórz listę rozwijaną i wybierz ciąg. Wybierz przycisk sąsiadujący **Konstruktor wyrażeń** , jeśli chcesz użyć co najmniej jednego wyrażenia regularnego w ciągu wyszukiwania. Aby uzyskać więcej informacji, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> Przycisk **konstruktora wyrażeń** zostanie włączony tylko w przypadku wybrania opcji **Użyj wyrażeń regularnych** w obszarze **Znajdź opcje**.

## <a name="replace-with"></a>Zamień na

Aby zamienić wystąpienia ciągu w polu **Znajdź** z innym ciągiem, wprowadź ciąg zamienny w polu **Zamień na** . Aby usunąć wystąpienia ciągu w polu **Znajdź** , pozostaw to pole puste. Otwórz listę, aby wyświetlić 20 ciągów, dla których Przeszukiwano ostatnio. Wybierz przycisk sąsiadujący **Konstruktor wyrażeń** , jeśli chcesz użyć co najmniej jednego wyrażenia regularnego w ciągu zamiennym. Aby uzyskać więcej informacji, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Szukaj w

Opcja wybrana z listy rozwijanej **Szukaj w** określa, czy **Zastąp w plikach** wyszukiwanie tylko w aktualnie aktywnych plikach, czy wyszukiwanie wszystkich plików przechowywanych w określonych folderach. Wybierz z listy zakres wyszukiwania, wpisz ścieżkę folderu, lub kliknij przycisk **Przeglądaj (...)** , aby wyświetlić okno dialogowe **Wybieranie folderów wyszukiwania** i wybrać zestaw folderów do przeszukania. Możesz również wpisać ścieżkę bezpośrednio do pola **Szukaj w** .

> [!NOTE]
> Jeśli wybrana opcja **Szukaj w** powoduje wyszukanie pliku, który został wyewidencjonowany z kontroli kodu źródłowego, przeszukiwany jest tylko wersja tego pliku, która została pobrana na komputer lokalny.

## <a name="find-options"></a>Opcje znajdowania

Można rozwinąć lub zwinąć sekcję **Znajdź opcje** . Można wybrać lub wyczyścić następujące opcje:

**Uwzględnij wielkość liter**

Gdy ta opcja jest zaznaczona, okna **Znajdź wyniki** będą wyświetlały tylko wystąpienia **szukanych** ciągów, które są dopasowane zarówno przez zawartość, jak i w przypadku. Na przykład wyszukiwanie "MyObject" z wybraną **wielkością liter** zwróci wartość "MyObject", ale nie "MyObject" lub "MyObject".

**Uwzględnij całe wyrazy**

Po wybraniu okna **Znajdź wyniki** będą wyświetlały tylko wystąpienia **szukanych** ciągów, które są dopasowane w kompletnych słowach. Na przykład wyszukiwanie "MyObject" zwróci wartość "MyObject", ale nie "CMyObject" lub "MyObjectC".

**Używanie wyrażeń regularnych**

Gdy to pole wyboru jest zaznaczone, można użyć notacji specjalnych do definiowania wzorców tekstu w polach tekstowych **Znajdź** lub **Zamień na** . Aby zapoznać się z listą tych notacji, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Sprawdź te typy plików**

Ta lista wskazuje typy plików do przeszukania **w katalogach wyszukiwania.** Jeśli to pole pozostanie puste, zostaną przeszukane wszystkie pliki znajdujące się w katalogach **wyszukiwania** . Wybierz dowolny element na liście, aby wprowadzić wstępnie skonfigurowany ciąg wyszukiwania, który będzie znajdował pliki tych konkretnych typów.

## <a name="result-options"></a>Opcje wyników

Można rozwinąć lub zwinąć sekcję **Opcje wyniku** . Można wybrać lub wyczyścić następujące opcje:

Okno **wyników wyszukiwania 1**

Po wybraniu wyniki bieżącego wyszukiwania zastąpią zawartość okna **Wyszukiwanie wyników 1** . To okno zostanie automatycznie otwarte w celu wyświetlenia wyników wyszukiwania. Aby otworzyć to okno ręcznie, wybierz pozycję **inne okna** w menu **Widok** i wybierz pozycję **Znajdź wyniki 1**.

Okno **wyników wyszukiwania 2**

Po wybraniu wyniki bieżącego wyszukiwania zastąpią zawartość okna **Wyszukiwanie wyników 2** . To okno zostanie automatycznie otwarte w celu wyświetlenia wyników wyszukiwania. Aby otworzyć to okno ręcznie, wybierz pozycję **inne okna** w menu **Widok** i wybierz pozycję **Znajdź wyniki 2**.

**Wyświetlaj tylko nazwy plików**

Gdy to pole wyboru jest zaznaczone, okna **Znajdź wyniki** wyświetlają pełne nazwy i ścieżki dla wszystkich plików, które zawierają ciąg wyszukiwania. Jednak wyniki nie uwzględniają wiersza kodu, w którym pojawia się ciąg. To pole wyboru jest dostępne tylko do **znajdowania w plikach** .

**Pozostaw zmodyfikowane pliki otwarte po zamianie wszystkich**

Po wybraniu tej czynności pozostawia otwarte wszystkie pliki, w których zostały wykonane zamiany, co umożliwia cofnięcie lub zapisanie zmian. Ograniczenia pamięci mogą ograniczyć liczbę plików, które mogą pozostać otwarte po operacji Zamień.

> [!CAUTION]
> Można użyć **Cofnij** tylko dla plików, które pozostaną otwarte do edycji. Jeśli ta opcja nie zostanie wybrana, pliki, które nie zostały jeszcze otwarte do edycji, pozostaną zamknięte i w tych plikach nie będzie dostępna opcja **Cofnij** .

## <a name="see-also"></a>Zobacz też

- [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)
- [Znajdź w plikach](../ide/find-in-files.md)
- [Visual Studio — Polecenia](../ide/reference/visual-studio-commands.md)
