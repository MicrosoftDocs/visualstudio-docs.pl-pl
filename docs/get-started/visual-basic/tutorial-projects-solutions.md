---
title: Projekty samouczków i rozwiązania Visual Basic
description: Dowiedz się, jak utworzyć rozwiązanie i projekt w Visual Studio jako Visual Basic deweloper.
ms.date: 12/12/2018
ms.technology: vs-ide-general
ms.custom:
- get-started
- SEO-VS-2020
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 4f27973fcfb76d019cff31787b117f05f8266ad8
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308184"
---
# <a name="learn-about-projects-and-solutions-using-visual-basic"></a>Dowiedz się więcej o projektach i rozwiązaniach korzystających z Visual Basic

W tym artykule wprowadzającym dowiesz się, co oznacza utworzenie rozwiązania *i* *projektu* w Visual Studio. Rozwiązanie to kontener, który służy do organizowania co najmniej jednego powiązanego projektu kodu, na przykład projektu biblioteki klas i odpowiadającego mu projektu testowego. Przyjrzymy się właściwościom projektu i niektórym plikom, które może zawierać. Utworzymy również odwołanie z jednego projektu do innego.

::: moniker range="vs-2017"

> [!TIP]
> Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/downloads) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2022"

> [!TIP]
> Jeśli jeszcze nie zainstalowano programu Visual Studio Preview, przejdź do strony pobierania Visual Studio [2022 w](https://visualstudio.microsoft.com/vs/preview/vs2022) wersji zapoznawczej, aby zainstalować ją bezpłatnie.

::: moniker-end

Skonstru będziemy konstruować rozwiązanie i projekt od podstaw jako ćwiczenie edukacyjne, aby zrozumieć koncepcję projektu. W przypadku ogólnego użycia Visual Studio prawdopodobnie będziesz używać niektórych różnych  szablonów projektów, które Visual Studio oferuje podczas tworzenia nowego projektu.

> [!NOTE]
> Rozwiązania i projekty nie są wymagane do tworzenia aplikacji w Visual Studio. Możesz również po prostu otworzyć folder zawierający kod i rozpocząć kodowanie, tworzenie i debugowanie. Na przykład klonowanie repozytorium [GitHub](https://github.com/) może nie zawierać Visual Studio i rozwiązań. Aby uzyskać więcej informacji, zobacz Develop code in Visual Studio without projects or solutions (Tworzenie kodu w [programie Visual Studio bez projektów i rozwiązań).](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

## <a name="solutions-and-projects"></a>Rozwiązania i projekty

Pomimo swojej nazwy rozwiązanie nie jest "odpowiedzią". Rozwiązanie to po prostu kontener używany przez Visual Studio do organizowania co najmniej jednego powiązanego projektu. Po otwarciu rozwiązania w Visual Studio automatycznie ładuje wszystkie projekty, które zawiera rozwiązanie.

### <a name="create-a-solution"></a>Tworzenie rozwiązania

Rozpoczniemy eksplorację od utworzenia pustego rozwiązania. Po poznaniu Visual Studio prawdopodobnie nie będziesz tworzyć pustych rozwiązań bardzo często. Podczas tworzenia nowego projektu program Visual Studio automatycznie tworzy rozwiązanie do jego przechowywu, jeśli nie ma jeszcze otwartego rozwiązania.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

1. Na pasku menu wybierz pozycję **Plik** > **Nowy** > **projekt.**

   Zostanie **otwarte okno dialogowe** Nowy projekt.

1. W okienku po lewej stronie **rozwiń pozycję Inne typy projektów,** a następnie wybierz **pozycję Visual Studio Solutions.** W środkowym okienku wybierz szablon **Puste rozwiązanie.** Nadaj **rozwiązaniu nazwę QuickSolution**, a następnie wybierz przycisk **OK.**

   ![Pusty szablon rozwiązania w Visual Studio](../media/tutorial-projects-new-solution.png)

   Strona **startowa** zostanie zamykana, a rozwiązanie Eksplorator rozwiązań **wyświetlone** po prawej stronie okna Visual Studio aplikacji. Prawdopodobnie będziesz często używać **Eksplorator rozwiązań,** aby przeglądać zawartość projektów.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie uruchamiania wybierz **pozycję Utwórz nowy projekt.**

3. Na stronie **Tworzenie nowego projektu** wprowadź puste **rozwiązanie** w polu wyszukiwania, wybierz szablon Puste **rozwiązanie,** a następnie wybierz pozycję **Dalej.**

   ![Pusty szablon rozwiązania w Visual Studio 2019 r.](../media/vs-2019/tutorial-projects-blank-solution-template.png)

4. Nazwij **rozwiązanie QuickSolution**, a następnie wybierz pozycję **Utwórz.**

   Rozwiązanie jest wyświetlane **Eksplorator rozwiązań** po prawej stronie okna Visual Studio aplikacji. Prawdopodobnie będziesz często używać **Eksplorator rozwiązań,** aby przeglądać zawartość projektów.

::: moniker-end

### <a name="add-a-project"></a>Dodawanie projektu

Teraz dodajmy nasz pierwszy projekt do rozwiązania. Zaczniemy od pustego projektu i dodamy do projektu potrzebne elementy.

::: moniker range="vs-2017"

1. W menu kontekstowym rozwiązania **"QuickSolution"** (Szybkie rozwiązanie) w menu Eksplorator rozwiązań prawym przyciskiem myszy wybierz pozycję Add New Project   > **(Dodaj nowy projekt).**

   Zostanie **otwarte okno dialogowe Dodawanie** nowego projektu.

1. W okienku po lewej stronie **rozwiń Visual Basic** i wybierz pozycję **Windows Desktop.** Następnie w środkowym okienku wybierz szablon **Pusty projekt (.NET Framework).** Nadaj **projektowi nazwę QuickDate**, a następnie wybierz **przycisk OK.**

   Projekt o nazwie QuickDate zostanie wyświetlony poniżej rozwiązania w **Eksplorator rozwiązań**. Obecnie zawiera pojedynczy plik o nazwie *App.config*.

   > [!NOTE]
   > Jeśli w okienku po lewej **stronie okna** dialogowego nie widzisz Visual Basic, musisz zainstalować pakiet Visual Studio **.NET** dla *aplikacji klasycznych.* Visual Studio korzysta z instalacji opartej na obciążeniach, aby zainstalować tylko te składniki, które są potrzebne do tego typu pisania. Łatwym sposobem zainstalowania nowego obciążenia jest wybranie linku **Otwórz** Instalator programu Visual Studio w lewym dolnym rogu okna dialogowego **Dodawanie** nowego projektu. Po Instalator programu Visual Studio wybierz obciążenie Tworzenie aplikacji klasycznych dla programu **.NET,** a następnie przycisk **Modyfikuj.**
   >
   > ![Otwórz Instalator programu Visual Studio link](media/tutorial-projects-open-installer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. W menu kontekstowym rozwiązania **"QuickSolution"** (Szybkie rozwiązanie) w menu Eksplorator rozwiązań prawym przyciskiem myszy wybierz pozycję Add New Project   > **(Dodaj nowy projekt).**

   Zostanie otwarte okno dialogowe z **komunikatem Add a new project (Dodaj nowy projekt).**

1. Wprowadź pusty tekst **w** polu wyszukiwania u góry, a następnie wybierz pozycję **Visual Basic** **w obszarze Język**.

1. Wybierz szablon **Pusty projekt (.NET Framework),** a następnie wybierz pozycję **Dalej.**

1. Nadaj **projektowi nazwę QuickDate,** a następnie wybierz **pozycję Utwórz**.

   Projekt o nazwie QuickDate zostanie wyświetlony poniżej rozwiązania w **Eksplorator rozwiązań**. Obecnie zawiera pojedynczy plik o nazwie *App.config*.

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Empty Project (.NET Framework),** musisz zainstalować pakiet roboczego tworzenie aplikacji klasycznych dla *Visual Studio* **.NET.** Visual Studio korzysta z instalacji opartej na obciążeniach, aby zainstalować tylko te składniki, które są potrzebne do tego typu pisania. Łatwym sposobem zainstalowania nowego obciążenia podczas tworzenia nowego projektu jest  wybranie linku Zainstaluj więcej narzędzi i funkcji pod tekstem Nie można znaleźć tego, czego **szukasz?**. Po Instalator programu Visual Studio wybierz obciążenie Tworzenie aplikacji klasycznych dla programu **.NET,** a następnie przycisk **Modyfikuj.**
   >
   > ![Link instalatora w programie Visual Studio 2019](../media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Dodawanie elementu do projektu

Mamy pusty projekt. Dodajmy plik kodu.

1. W menu kontekstowym lub prawym przyciskiem myszy projektu **QuickDate** w **programie Eksplorator rozwiązań** wybierz **pozycję Dodaj** nowy  >  **element**.

   Zostanie **otwarte okno dialogowe Dodawanie** nowego elementu.

1. Rozwiń **pozycję Wspólne elementy,** a następnie wybierz **pozycję Kod**. W środkowym okienku wybierz **szablon Element** klasy. Nadaj klasie **nazwę Calendar,** a następnie wybierz **przycisk** Dodaj.

   Do projektu zostanie dodany plik o nazwie *Calendar.vb.* *.vb* na końcu to rozszerzenie pliku, które jest nadane do Visual Basic kodu. Plik zostanie wyświetlony w hierarchii projektu wizualizacji w **Eksplorator rozwiązań**, a jego zawartość zostanie otwarta w edytorze.

1. Zastąp zawartość pliku *Calendar.vb* następującym kodem:

   ```vb
   Class Calendar
       Public Shared Function GetCurrentDate() As Date
           Return DateTime.Now.Date
       End Function
   End Class
   ```

   Klasa `Calendar` zawiera pojedynczą funkcję `GetCurrentDate` , która zwraca bieżącą datę.

1. Otwórz właściwości projektu, klikając dwukrotnie pozycję **Mój projekt** w **Eksplorator rozwiązań**. Na karcie **Aplikacja** zmień typ aplikacji **na** **Biblioteka klas**. Ten krok jest niezbędny do pomyślnego skompilowania projektu.

1. Skompilować projekt, klikając prawym przyciskiem myszy pozycję **QuickDate** w Eksplorator rozwiązań **i** wybierając polecenie **Build (Kompilacja).** W oknie Dane wyjściowe powinien zostać wyświetlony komunikat o **pomyślnej kompilacji.**

## <a name="add-a-second-project"></a>Dodawanie drugiego projektu

Rozwiązania często zawierają więcej niż jeden projekt, a często te projekty odwołują się do siebie nawzajem. Niektóre projekty w rozwiązaniu mogą być bibliotekami klas, niektóre aplikacjami wykonywalnymi, a niektóre mogą być projektami testów jednostkowych lub witrynami internetowymi.

Dodajmy projekt testu jednostkowego do naszego rozwiązania. Tym razem zaczniemy od szablonu projektu, aby nie trzeba było dodawać do projektu dodatkowego pliku kodu.

1. W menu kontekstowym rozwiązania **"QuickSolution"** (Szybkie rozwiązanie) w menu Eksplorator rozwiązań prawym przyciskiem myszy wybierz pozycję Add New Project    >  **(Dodaj nowy projekt).**

::: moniker range="Vs-2017"

2. W okienku po lewej **stronie rozwiń Visual Basic** i wybierz **kategorię Test.** W środkowym okienku wybierz szablon **projektu Unit Test Project (.NET Framework).** Nazwij projekt **QuickTest**, a następnie wybierz przycisk **OK.**

   Drugi projekt jest dodawany do **Eksplorator rozwiązań**, a w edytorze zostanie otwarty plik o nazwie *UnitTest1.vb.*

   ![Visual Studio Eksplorator rozwiązań z dwoma projektami](media/tutorial-projects-solution-explorer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. W **oknie dialogowym Dodawanie nowego** projektu  wprowadź test jednostkowy tekstu w polu wyszukiwania u góry, a następnie wybierz pozycję **Visual Basic** obszarze **Język**.

3. Wybierz szablon **projektu Unit Test Project (.NET Framework),** a następnie wybierz pozycję **Dalej.**

4. Nazwij projekt **QuickTest**, a następnie wybierz pozycję **Utwórz.**

   Drugi projekt jest dodawany do **Eksplorator rozwiązań**, a w edytorze zostanie otwarty plik o nazwie *UnitTest1.vb.*

::: moniker-end

## <a name="add-a-project-reference"></a>Dodawanie odwołania do projektu

Użyjemy nowego projektu testu jednostkowego do przetestowania naszej metody w projekcie **QuickDate,** więc musimy dodać odwołanie do tego projektu. Powoduje to utworzenie *zależności kompilacji* między dwoma projektami, co oznacza, że podczas kompilowania rozwiązania funkcja **QuickDate** jest kompilowana przed **quicktestem.**

1. Wybierz węzeł **Odwołania** w **projekcie QuickTest,** a następnie z menu kontekstowego lub kliknij prawym przyciskiem myszy pozycję **Dodaj odwołanie.**

   ![Menu Dodaj odwołanie](media/tutorial-projects-add-reference-vb.png)

   Zostanie **otwarte okno dialogowe** Menedżer odwoływać.

1. W okienku po lewej stronie **rozwiń pozycję Projekty** i wybierz **pozycję Rozwiązanie.** W środkowym okienku zaznacz pole wyboru obok opcji **QuickDate (QuickDate),** a następnie wybierz **przycisk OK.**

   Zostanie dodane odwołanie do **projektu QuickDate.**

## <a name="add-test-code"></a>Dodawanie kodu testowego

1. Teraz dodamy kod testowy do Visual Basic kodu. Zastąp zawartość pliku *UnitTest1.vb* poniższym kodem.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(Date.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   Pod niektórymi kodami zostanie wyświetlony czerwony zygieł. Naprawimy ten błąd, czynimy projekt testowy przyjaznym [zestawem](/dotnet/visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies) w **projekcie QuickDate.**

1. Po powrocie do projektu **QuickDate** otwórz plik *Calendar.vb,* jeśli nie został jeszcze otwarty, i dodaj następującą instrukcje [Imports](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) oraz atrybut , aby usunąć błąd w <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> projekcie testowym.

   ```vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("QuickTest")>
   ```

   Plik kodu powinien wyglądać tak:

   ![Kod Visual Basic](media/tutorial-projects-code-vb.png)

## <a name="project-properties"></a>Właściwości projektu

Wiersz w pliku *Calendar.vb* zawierający atrybut odwołuje się do nazwy <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> zestawu (nazwy pliku) projektu **QuickTest.** Nazwa zestawu nie zawsze może być taka sama jak nazwa projektu. Aby znaleźć nazwę zestawu projektu, otwórz właściwości projektu.

1. W **Eksplorator rozwiązań** wybierz projekt **QuickTest.** W menu kontekstowym lub prawym przyciskiem myszy wybierz pozycję **Właściwości** lub po prostu naciśnij **klawisz Alt** + **Enter**. (Możesz również kliknąć dwukrotnie pozycję **Mój projekt w** **Eksplorator rozwiązań**).

   Strony *właściwości projektu* otwarte na **karcie** Aplikacja. Strony właściwości zawierają różne ustawienia projektu. Zwróć uwagę, że nazwa zestawu projektu **QuickTest** to rzeczywiście "QuickTest". Jeśli chcesz ją zmienić, możesz to zrobić w tym miejscu. Następnie podczas kompilowania projektu testowego nazwa wynikowego pliku binarnego zmieni się *zQuickTest.dll* na wybraną przez Ciebie.

   ![Właściwości projektu](../media/tutorial-projects-properties.png)

1. Zapoznaj się z innymi kartami stron właściwości projektu, takimi jak **Compile** (Kompilacja) **i Settings (Ustawienia).** Te karty są różne dla różnych typów projektów.

## <a name="optional-run-the-test"></a>(Opcjonalnie) Uruchamianie testu

Jeśli chcesz sprawdzić, czy test jednostkowy działa, wybierz pozycję **Testuj** wszystkie testy  >    >   na pasku menu. Zostanie otwarte okno **Eksplorator testów.** Powinien zostać wyświetlony test **TestGetCurrentDate** przebiegł pomyślnie.

![Eksplorator tekstu w programie Visual Studio z pomyślnie przekazanym testem](../media/tutorial-projects-test-explorer.png)

> [!TIP]
> Jeśli **Eksplorator testów** nie zostanie otwarty automatycznie, otwórz go, wybierając pozycję Przetestuj   >    >  **Eksploratora testów** systemu Windows na pasku menu.

## <a name="next-steps"></a>Następne kroki

Jeśli chcesz bardziej eksplorować Visual Studio, rozważ utworzenie aplikacji, korzystając z jednego z samouczków Visual Basic [samouczków.](index.yml)

## <a name="see-also"></a>Zobacz też

- [Tworzenie projektów i rozwiązań](../../ide/creating-solutions-and-projects.md)
- [Zarządzanie właściwościami projektów i rozwiązań](../../ide/managing-project-and-solution-properties.md)
- [Zarządzanie odwołaniami w projekcie](../../ide/managing-references-in-a-project.md)
- [Tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [omówienie Visual Studio IDE](../../get-started/visual-studio-ide.md)
