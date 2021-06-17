---
title: Wprowadzenie do projektów i rozwiązań
description: Dowiedz się więcej na temat różnic między projektami i rozwiązaniami oraz sposobu ich używania w Visual Studio.
ms.date: 11/17/2020
ms.technology: vs-ide-general
ms.custom:
- acquisition
- get-started
- SEO-VS-2020
ms.topic: tutorial
f1_keywords:
- project.addnewitem
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 11db2d793f284557f709a4f72362cfc89a77a059
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113035"
---
# <a name="introduction-to-projects-and-solutions"></a>Wprowadzenie do projektów i rozwiązań

W tym artykule wprowadzającym dowiesz się, co oznacza utworzenie rozwiązania *i* *projektu* w Visual Studio. Rozwiązanie to kontener, który służy do organizowania co najmniej jednego powiązanego projektu kodu, na przykład projektu biblioteki klas i odpowiadającego mu projektu testowego. Przyjrzymy się właściwościom projektu i niektórym plikom, które może on zawierać. Utworzymy również odwołanie z jednego projektu do innego.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano aplikacji Visual Studio, przejdź [](https://visualstudio.microsoft.com/downloads) do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

Skonstru będziemy konstruować rozwiązanie i projekt od podstaw jako ćwiczenie edukacyjne, aby zrozumieć koncepcję projektu. W przypadku ogólnego użycia Visual Studio prawdopodobnie będziesz używać niektórych różnych  szablonów projektów, które Visual Studio oferuje podczas tworzenia nowego projektu.

> [!NOTE]
> Rozwiązania i projekty nie są wymagane do tworzenia aplikacji w Visual Studio. Możesz również po prostu otworzyć folder, który zawiera kod, i rozpocząć kodowanie, tworzenie i debugowanie. Na przykład klonowanie repozytorium [GitHub](https://github.com/) może nie zawierać Visual Studio i rozwiązań. Aby uzyskać więcej informacji, zobacz Develop code in Visual Studio without projects or solutions (Tworzenie kodu [w programie Visual Studio bez projektów i rozwiązań).](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

## <a name="solutions-and-projects"></a>Rozwiązania i projekty

Pomimo swojej nazwy rozwiązanie nie jest "odpowiedzią". Rozwiązanie to po prostu kontener używany przez Visual Studio do organizowania co najmniej jednego powiązanego projektu. Po otwarciu rozwiązania w Visual Studio automatycznie ładuje wszystkie projekty, które zawiera rozwiązanie.

### <a name="create-a-solution"></a>Tworzenie rozwiązania

Rozpoczniemy eksplorację od utworzenia pustego rozwiązania. Po poznaniu Visual Studio prawdopodobnie nie będziesz tworzyć pustych rozwiązań bardzo często. Podczas tworzenia nowego projektu program Visual Studio automatycznie tworzy rozwiązanie do jego przechowywu, jeśli nie ma jeszcze otwartego rozwiązania.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

1. Na górnym pasku menu wybierz pozycję **File** New Project > **(Nowy projekt** > **pliku).**

   Zostanie **otwarte okno dialogowe** Nowy projekt.

1. W okienku po lewej stronie **rozwiń pozycję Inne typy projektów,** a następnie **wybierz pozycję Visual Studio Solutions.** W środkowym okienku wybierz szablon **Puste** rozwiązanie. Nazwij **rozwiązanie QuickSolution,** a następnie wybierz **przycisk OK.**

   ![Pusty szablon rozwiązania w programie Visual Studio 2017](media/tutorial-projects-new-solution.png "Szablon Puste rozwiązanie w Visual Studio 2017 r.")

   Strona **startowa** zostanie zamykana, a rozwiązanie Eksplorator rozwiązań **wyświetlone** po prawej stronie okna Visual Studio aplikacji. Prawdopodobnie będziesz często używać **Eksplorator rozwiązań,** aby przeglądać zawartość projektów.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie uruchamiania wybierz **pozycję Utwórz nowy projekt.**

3. Na stronie Tworzenie nowego projektu  wprowadź puste rozwiązanie w polu wyszukiwania, wybierz szablon **Puste rozwiązanie,** **a** następnie wybierz pozycję **Dalej.**

   ![Pusty szablon rozwiązania w Visual Studio 2019 r.](media/vs-2019/tutorial-projects-blank-solution-template.png "Szablon Puste rozwiązanie w Visual Studio 2019 r.")

    > [!TIP]
    > Jeśli masz zainstalowanych kilka obciążeń, szablon **Puste rozwiązanie** może nie być wyświetlany na początku listy wyników wyszukiwania. Spróbuj przewinąć do sekcji Inne wyniki w **oparciu o sekcję** wyszukiwania na liście. Powinien on zostać wyświetlony na tej stronie.

4. Nazwij **rozwiązanie QuickSolution**, a następnie wybierz pozycję **Utwórz**.

   Rozwiązanie jest wyświetlane **Eksplorator rozwiązań** po prawej stronie okna Visual Studio aplikacji. Prawdopodobnie będziesz często używać **Eksplorator rozwiązań,** aby przeglądać zawartość projektów.

::: moniker-end

### <a name="add-a-project"></a>Dodawanie projektu

Teraz dodajmy nasz pierwszy projekt do rozwiązania. Zaczniemy od pustego projektu i dodamy do projektu potrzebne elementy.

::: moniker range="vs-2017"

1. W menu kontekstowym rozwiązania **"QuickSolution"** (Szybkie rozwiązanie) w menu Eksplorator rozwiązań prawym przyciskiem myszy wybierz pozycję **Add** New Project  > **(Dodaj nowy projekt).**

   Zostanie **otwarte okno dialogowe Dodawanie** nowego projektu.

1. W okienku po lewej stronie **rozwiń pozycję Visual C#** i wybierz pozycję **Windows Desktop.** Następnie w środkowym okienku wybierz szablon **Pusty projekt (.NET Framework).** Nadaj **projektowi nazwę QuickDate**, a następnie wybierz przycisk **OK.**

   Projekt o nazwie QuickDate zostanie wyświetlony poniżej rozwiązania w **Eksplorator rozwiązań**. Obecnie zawiera pojedynczy plik o nazwie *App.config*.

   > [!NOTE]
   > Jeśli nie widzisz programu **Visual C#** w lewym okienku okna dialogowego, musisz zainstalować pakiet projektowy aplikacji klasycznych dla Visual Studio **.NET.** Visual Studio instalacji opartej na obciążeniach jest używana do instalowania tylko tych składników, które są potrzebne do tego typu pisania. Łatwym sposobem zainstalowania nowego obciążenia jest wybranie linku **Otwórz** Instalator programu Visual Studio w lewym dolnym rogu okna dialogowego **Dodawanie nowego** projektu. Po Instalator programu Visual Studio wybierz obciążenie Tworzenie aplikacji klasycznych dla programu **.NET,** a następnie przycisk **Modyfikuj.**
   >
   > ![Otwórz Instalator programu Visual Studio link](media/tutorial-projects-open-installer.png "Link Otwórz Instalator programu Visual Studio w oknie dialogowym Dodawanie nowego projektu w programie Visual Studio 2017.")

::: moniker-end

::: moniker range=">=vs-2019"

1. W menu kontekstowym rozwiązania **"QuickSolution"** (Szybkie rozwiązanie) w menu Eksplorator rozwiązań prawym przyciskiem myszy wybierz pozycję **Add** New Project  > **(Dodaj nowy projekt).**

   Zostanie otwarte okno dialogowe z **komunikatem Dodaj nowy projekt**.

1. Wprowadź pusty tekst **w** polu wyszukiwania u góry, a następnie wybierz pozycję **C#** w obszarze **Język**.

1. Wybierz szablon **Pusty projekt (.NET Framework),** a następnie wybierz pozycję **Dalej.**

1. Nadaj **projektowi nazwę QuickDate,** a następnie wybierz **pozycję Utwórz**.

   Projekt o nazwie QuickDate zostanie wyświetlony poniżej rozwiązania w **Eksplorator rozwiązań**. Obecnie zawiera pojedynczy plik o nazwie *App.config*.

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Empty Project (.NET Framework),** musisz zainstalować pakiet Visual Studio **.NET.** Visual Studio instalacji opartej na obciążeniach jest używana do instalowania tylko tych składników, które są potrzebne do tego typu pisania.
   >
   >Łatwym sposobem zainstalowania nowego obciążenia podczas tworzenia nowego projektu jest  wybranie linku Zainstaluj więcej narzędzi i funkcji pod tekstem Nie można znaleźć tego, czego **szukasz?**. Po Instalator programu Visual Studio wybierz obciążenie Tworzenie aplikacji klasycznych dla programu **.NET,** a następnie przycisk **Modyfikuj.**
   >
   > ![Otwórz Instalator programu Visual Studio link](media/vs-2019/tutorial-projects-open-installer.png "Link Otwórz Instalator programu Visual Studio w oknie dialogowym Tworzenie nowego projektu w Visual Studio.")

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Dodawanie elementu do projektu

Mamy pusty projekt. Dodajmy plik kodu.

1. W menu kontekstowym lub prawym przyciskiem myszy projektu **QuickDate** w **programie Eksplorator rozwiązań** wybierz **pozycję Dodaj** nowy  >  **element**.

   Zostanie **otwarte okno dialogowe Dodawanie** nowego elementu.

1. Rozwiń **pozycję Elementy Visual C#,** a następnie wybierz **pozycję Kod**. W środkowym okienku wybierz **szablon Element** klasy. Nadaj klasie **nazwę Calendar,** a następnie wybierz **przycisk** Dodaj.

   Do projektu zostanie dodany plik o nazwie *Calendar.cs.* Plik *cs* na końcu jest rozszerzeniem pliku, które jest nadane plikom kodu języka C#. Plik zostanie wyświetlony w hierarchii projektu wizualizacji w **Eksplorator rozwiązań**, a jego zawartość zostanie otwarta w edytorze.

1. Zastąp zawartość pliku *Calendar.cs* następującym kodem:

   ```csharp
   using System;

   namespace QuickDate
   {
       internal class Calendar
       {
           static void Main(string[] args)
           {
               DateTime now = GetCurrentDate();
               Console.WriteLine($"Today's date is {now}");
               Console.ReadLine();
           }

           internal static DateTime GetCurrentDate()
           {
               return DateTime.Now.Date;
           }
       }
   }
   ```

   Nie musisz rozumieć, jak działa kod, ale jeśli chcesz, możesz uruchomić program, naciskając klawisz **Ctrl** F5 i zobaczyć, że drukuje on dzisiejszą datę w oknie konsoli (lub standardowych danych +  wyjściowych).

## <a name="add-a-second-project"></a>Dodawanie drugiego projektu

Rozwiązania często zawierają więcej niż jeden projekt, a często te projekty odwołują się do siebie nawzajem. Niektóre projekty w rozwiązaniu mogą być bibliotekami klas, niektóre aplikacjami wykonywalnymi, a niektóre mogą być projektami testów jednostkowych lub witrynami internetowymi.

Dodajmy projekt testu jednostkowego do naszego rozwiązania. Tym razem zaczniemy od szablonu projektu, aby nie trzeba było dodawać do projektu dodatkowego pliku kodu.

1. W menu kontekstowym rozwiązania **"QuickSolution"** (Szybkie rozwiązanie) w menu Eksplorator rozwiązań prawym przyciskiem myszy wybierz pozycję **Add** New Project   >  **(Dodaj nowy projekt).**

::: moniker range="vs-2017"

2. W okienku po lewej stronie **rozwiń pozycję Visual C#** i wybierz **kategorię Test.** W środkowym okienku wybierz **szablon projektu MSTest Test Project (.NET Core).** Nadaj **projektowi nazwę QuickTest**, a następnie wybierz przycisk **OK.**

   Drugi projekt jest dodawany do **Eksplorator rozwiązań**, a w edytorze zostanie otwarty plik o nazwie *UnitTest1.cs.*

   ![Visual Studio Eksplorator rozwiązań z dwoma projektami](media/tutorial-projects-solution-explorer.png "Eksplorator rozwiązań z dwoma projektami w Visual Studio 2017 r.")

::: moniker-end

::: moniker range=">=vs-2019"

2. W **oknie dialogowym** Dodawanie nowego projektu wprowadź **test** jednostkowy tekstu w polu wyszukiwania u góry, a następnie wybierz pozycję **C#** w obszarze **Język**.

3. Wybierz szablon **projektu projektu testów** jednostkowych dla programu .NET Core, a następnie wybierz pozycję **Dalej.**

   > [!NOTE]
   > Począwszy od Visual Studio 2019 r. w wersji 16.9 nazwa szablonu projektu MSTest zmieniła się z **MSTest Unit Test Project (.NET Core)** na **Unit Test Project**. W tej aktualizacji zmieniono kilka kroków tworzenia projektu.

4. Nadaj **projektowi nazwę QuickTest**, a następnie wybierz pozycję **Dalej.**

5. Wybierz zalecaną platformę docelową (.NET Core 3.1) lub .NET 5, a następnie wybierz pozycję **Utwórz.**

   Drugi projekt jest dodawany do **Eksplorator rozwiązań**, a w edytorze zostanie otwarty plik o nazwie *UnitTest1.cs.*

   ![Visual Studio Eksplorator rozwiązań z dwoma projektami](media/vs-2019/tutorial-projects-solution-explorer.png "Eksplorator rozwiązań z dwoma projektami w Visual Studio.")

::: moniker-end

## <a name="add-a-project-reference"></a>Dodawanie odwołania do projektu

Użyjemy nowego projektu testu jednostkowego do przetestowania naszej metody w projekcie **QuickDate,** dlatego musimy dodać odwołanie do tego projektu. Powoduje to utworzenie *zależności kompilacji* między dwoma projektami, co oznacza, że podczas kompilowania rozwiązania funkcja **QuickDate** jest kompilowana przed szybkim **testem**.

::: moniker range="vs-2017"

1. Wybierz węzeł **Zależności** w **projekcie QuickTest,** a następnie z menu kontekstowego lub kliknij prawym przyciskiem myszy pozycję **Dodaj odwołanie.**

   Zostanie **otwarte okno dialogowe** Menedżer odwoływać.

1. W okienku po lewej stronie **rozwiń pozycję Projekty** i wybierz **pozycję Rozwiązanie.** W środkowym okienku zaznacz pole wyboru obok opcji **QuickDate**,a następnie wybierz przycisk **OK.**

   Zostanie dodane odwołanie do **projektu QuickDate.**

   ![Zrzut ekranu przedstawiający Eksplorator rozwiązań z odwołaniem do projektu w Visual Studio](media/vs-2019/tutorial-projects-solution-explorer-reference.png "Zrzut ekranu przedstawiający Eksplorator rozwiązań odwołanie do projektu w Visual Studio.")

::: moniker-end

::: moniker range="vs-2019"

1. Wybierz węzeł **Zależności w** **projekcie QuickTest,** a następnie z menu kontekstowego lub kliknij prawym przyciskiem myszy pozycję **Dodaj odwołanie do projektu...**.

   Zostanie **otwarte okno dialogowe** Menedżer odwoływać.

1. W okienku po lewej stronie **rozwiń pozycję Projekty**, a następnie wybierz **pozycję Rozwiązanie.** W środkowym okienku zaznacz pole wyboru obok opcji **QuickDate**,a następnie wybierz przycisk **OK.**

   Zostanie dodane odwołanie do **projektu QuickDate.**

   ![Zrzut ekranu przedstawiający Eksplorator rozwiązań odwołanie do projektu w Visual Studio 2019 r.](media/vs-2019/tutorial-projects-solution-explorer-reference.png)

::: moniker-end

## <a name="add-test-code"></a>Dodawanie kodu testowego

1. Teraz dodamy kod testowy do pliku kodu testowego języka C#. Zastąp zawartość pliku *UnitTest1.cs* następującym kodem:

   ```csharp
   using System;
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace QuickTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestGetCurrentDate()
           {
               Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate());
           }
       }
   }
   ```

   Pod niektórym kodem zostanie wyświetlony czerwony zygieł. Naprawimy ten błąd, czynimy projekt testowy przyjaznym [zestawem](/dotnet/standard/assembly/friend-assemblies) w **projekcie QuickDate.**

1. Po powrocie do **projektu QuickDate** otwórz plik *Calendar.cs,* jeśli nie został jeszcze otwarty. Dodaj następującą [instrukcje using](/dotnet/csharp/language-reference/keywords/using-statement) i atrybut na początku pliku, aby usunąć <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> błąd w projekcie testowym.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Plik kodu powinien wyglądać tak:

   ![Kod CSharp](media/tutorial-projects-cs-code.png "Fragment kodu z sekcji Dodawanie kodu testowego w tym artykule.")

## <a name="project-properties"></a>Właściwości projektu

Wiersz w pliku *Calendar.cs,* który zawiera atrybut, odwołuje się do nazwy <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> zestawu (nazwy pliku) projektu **QuickTest.** Nazwa zestawu nie zawsze może być taka sama jak nazwa projektu. Aby znaleźć nazwę zestawu projektu, otwórz właściwości projektu.

1. W **Eksplorator rozwiązań** wybierz projekt **QuickTest.** W menu kontekstowym lub prawym przyciskiem myszy wybierz pozycję **Właściwości** lub po prostu naciśnij **klawisz Alt** + **Enter.**

   Strony *właściwości projektu* otwarte na **karcie** Aplikacja. Strony właściwości zawierają różne ustawienia projektu. Zwróć uwagę, że nazwa zestawu projektu **QuickTest** to w rzeczywistości "QuickTest". Jeśli chcesz ją zmienić, możesz to zrobić w tym miejscu. Następnie podczas kompilowania projektu testowego nazwa wynikowego pliku binarnego zmieni się *zQuickTest.dll* na wybraną.

   ![Właściwości projektu](media/tutorial-projects-netcore-properties.png "Okno dialogowe Właściwości projektu w Visual Studio.")

1. Zapoznaj się z niektórymi innymi kartami stron właściwości projektu, takimi jak **Kompilacja** i **Debugowanie.** Te karty są różne dla różnych typów projektów.

## <a name="next-steps"></a>Następne kroki

::: moniker range="vs-2017"

Jeśli chcesz sprawdzić, czy test jednostkowy działa, wybierz pozycję **Testuj** wszystkie testy  >    >   na pasku menu. Zostanie otwarte okno **o nazwie Eksplorator** testów. Powinien zostać wyświetlony test **TestGetCurrentDate** przebiegł pomyślnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli chcesz sprawdzić, czy test jednostkowy działa, wybierz pozycję **Testuj** wszystkie testy  >   na pasku menu. Zostanie otwarte okno **o nazwie Eksplorator** testów. Powinien zostać wyświetlony test **TestGetCurrentDate** przebiegł pomyślnie.

::: moniker-end

![Eksplorator testów w programie Visual Studio z pomyślnie przekazanym testem](media/tutorial-projects-test-explorer.png "Eksplorator testów w Visual Studio z pomyślnie przekazanym testem.")

::: moniker range="vs-2017"

> [!TIP]
> Jeśli **Eksplorator testów** nie zostanie otwarty automatycznie, otwórz go, wybierając pozycję **Testuj**  >    >  **Eksploratora testów** systemu Windows na pasku menu.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Jeśli **Eksplorator testów** nie zostanie otwarty automatycznie, otwórz go, wybierając pozycję **Eksplorator**  >  **testów** na pasku menu.

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Praca z projektami i rozwiązaniami](../ide/creating-solutions-and-projects.md)
- [Zarządzanie właściwościami projektów i rozwiązań](../ide/managing-project-and-solution-properties.md)
- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
- [Tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE — omówienie](../get-started/visual-studio-ide.md)
