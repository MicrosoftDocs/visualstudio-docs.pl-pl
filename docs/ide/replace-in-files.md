---
title: Znajdowanie i zamienianie w plikach
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585629"
---
# <a name="replace-in-files"></a>Zastąp w plikach

**Zamień w plikach** pozwala na wyszukiwanie kodu określonego zestawu plików dla ciągu lub wyrażenia i zmienić niektóre lub wszystkie znalezione dopasowania. Znalezione dopasowania i podjęte akcje są wyświetlane w oknie **Znajdź wyniki** wybranym w obszarze **Opcje wyników**.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą różnić się od tych opisanych w **Pomocy** w zależności od aktywnych ustawień lub wersji. Aby zmienić ustawienia, na przykład na **Ustawienia ogólne** lub **Visual C++,** wybierz pozycję Ustawienia**importu i eksportu** **narzędzi,** > a następnie wybierz pozycję **Resetuj wszystkie ustawienia**.

Można użyć dowolnej z następujących metod **wyświetlania opcji Zamień w** oknie Pliki w oknie **Znajdź i zamień.**

## <a name="to-display-replace-in-files"></a>Aby wyświetlić pozycję Zamień w plikach

1. W menu **Edycja** rozwiń pozycję **Znajdź i zamień**.

2. Wybierz **pozycję Zamień w plikach**.

   — lub —

   Jeśli okno **Znajdź i zamień** jest już otwarte, na pasku narzędzi wybierz pozycję **Zamień w pliku**.

## <a name="find-what"></a>Znajdź

Aby wyszukać nowy ciąg tekstowy lub wyrażenie, należy określić je w polu. Aby wyszukać dowolny z 20 ciągów, które ostatnio wyszukiwano, otwórz listę rozwijaną i wybierz ciąg. Wybierz sąsiedni przycisk **Konstruktora wyrażeń,** jeśli chcesz użyć jednego lub więcej wyrażeń regularnych w ciągu wyszukiwania. Aby uzyskać więcej informacji, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> Przycisk **Konstruktora wyrażeń** będzie włączony tylko wtedy, gdy w obszarze **Opcje znajdowania**wybrano opcję **Użyj wyrażeń regularnych** .

## <a name="replace-with"></a>Zamień na

Aby zastąpić wystąpienia ciągu w polu **Znajdź, który** ciąg jest inny, wprowadź ciąg zastępczy w polu **Zamień** na. Aby usunąć wystąpienia ciągu w polu **Znajdź,** pozostaw to pole puste. Otwórz listę, aby wyświetlić 20 ciągów, dla których ostatnio wyszukiwano. Wybierz sąsiedni przycisk **Konstruktora wyrażeń,** jeśli chcesz użyć jednego lub więcej wyrażeń regularnych w ciągu zastępczym. Aby uzyskać więcej informacji, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="look-in"></a>Zajrzyj do

Opcja wybrana z listy rozwijanej **Szukaj w** określa, czy **opcja Zamień w plikach** wyszukuje tylko w aktualnie aktywnych plikach, czy przeszukuje wszystkie pliki przechowywane w określonych folderach. Wybierz zakres wyszukiwania z listy, wpisz ścieżkę folderu lub kliknij przycisk **Przeglądaj (...)** aby wyświetlić okno dialogowe **Wybieranie folderów wyszukiwania** i wybierz zestaw folderów do przeszukania. Można również wpisać ścieżkę bezpośrednio w polu **Szukaj w.**

> [!NOTE]
> Jeśli wybrana opcja **Szukaj w** powoduje przeszukanie pliku, który został wyewidencjonowany z kontroli kodu źródłowego, przeszukiwana jest tylko wersja tego pliku pobrana na komputer lokalny.

## <a name="find-options"></a>Znajdź opcje

Można rozwinąć lub zwinąć sekcję **Opcje znajdowania.** Można wybrać lub wyczyścić następujące opcje:

**Uwzględnij wielkość liter**

Po wybraniu tej opcji okna **Znajdź wyniki** będą wyświetlane tylko wystąpienia ciągu **Znajdź,** które są dopasowane zarówno według zawartości, jak i według przypadku. Na przykład wyszukiwanie "MyObject" z wybraną **sprawą Match** zwróci "MyObject", ale nie "myobject" lub "MYOBJECT".

**Dopasuj całe słowo**

Po wybraniu tej opcji w oknach **Znajdź wyniki** będą wyświetlane tylko wystąpienia ciągu **Znajdź,** które są dopasowane w pełnych słowach. Na przykład wyszukiwanie "MyObject" zwróci "MyObject", ale nie "CMyObject" lub "MyObjectC".

**Używanie wyrażeń regularnych**

Gdy to pole wyboru jest zaznaczone, można użyć specjalnych notacji do zdefiniowania wzorców tekstu w polach tekstowych **Znajdź, co** lub **Zamień na** nią. Aby uzyskać listę tych notacji, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Spójrz na te typy plików**

Ta lista wskazuje typy plików do przeszukania w katalogach **Szukaj w.** Jeśli to pole pozostanie puste, zostaną przeszukane wszystkie pliki w katalogach **Szukaj w** katalogach. Wybierz dowolny element na liście, aby wprowadzić wstępnie skonfigurowany ciąg wyszukiwania, który znajdzie pliki tych typów.

## <a name="result-options"></a>Opcje wyników

Można rozwinąć lub zwinąć sekcję **Opcje wyników.** Można wybrać lub wyczyścić następujące opcje:

**Znajdź wyniki 1** okno

Po wybraniu tej opcji wyniki bieżącego wyszukiwania zastąpią zawartość okna **Znajdź wyniki 1.** To okno zostanie otwarte automatycznie, aby wyświetlić wyniki wyszukiwania. Aby ręcznie otworzyć to okno, wybierz **polecenie Inne okna** z menu **Widok** i wybierz polecenie Znajdź **wyniki 1**.

**Znajdź wyniki 2** okno

Po wybraniu tej opcji wyniki bieżącego wyszukiwania zastąpią zawartość okna **Znajdź wyniki 2.** To okno zostanie otwarte automatycznie, aby wyświetlić wyniki wyszukiwania. Aby ręcznie otworzyć to okno, wybierz **polecenie Inne okna** z menu **Widok** i wybierz polecenie Znajdź **wyniki 2**.

**Wyświetlanie tylko nazw plików**

Gdy to pole wyboru jest zaznaczone, okna **Znajdź wyniki** wyświetlają pełne nazwy i ścieżki dla wszystkich plików zawierających ciąg wyszukiwania. Jednak wyniki nie zawierają wiersza kodu, w którym pojawia się ciąg. To pole wyboru jest dostępne tylko w polu **Znajdź w plikach.**

**Po zastąp wszystkie zmodyfikowane pliki**

Po wybraniu tej opcji pozostawia otwarte wszystkie pliki, w których dokonano zamienników, dzięki czemu można cofnąć lub zapisać zmiany. Ograniczenia pamięci mogą ograniczać liczbę plików, które mogą pozostać otwarte po operacji wymiany.

> [!CAUTION]
> Funkcji **Cofnij** można używać tylko w plikach, które pozostają otwarte do edycji. Jeśli ta opcja nie jest zaznaczona, pliki, które nie były jeszcze otwarte do edycji, pozostaną zamknięte, a w tych plikach nie będzie dostępna żadna opcja **Cofnij.**

## <a name="see-also"></a>Zobacz też

- [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)
- [Znajdowanie w plikach](../ide/find-in-files.md)
- [Polecenia programu Visual Studio](../ide/reference/visual-studio-commands.md)
