---
title: Wprowadzenie do projektów i rozwiązań
ms.date: 02/24/2020
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da2fc196f687e2335933794a578f507dafbc6de3
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579975"
---
# <a name="learn-about-projects-and-solutions"></a>Dowiedz się więcej o projektach i rozwiązaniach

W tym artykule wprowadzającym zbadamy, co to znaczy utworzyć *rozwiązanie* i *projekt* w programie Visual Studio. Rozwiązanie jest kontenerem, który jest używany do organizowania jednego lub więcej powiązanych projektów kodu, na przykład projektu biblioteki klas i odpowiedniego projektu testowego. Przyjrzymy się właściwości projektu i niektóre pliki, które mogą zawierać. Utworzymy również odwołanie z jednego projektu do drugiego.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.

::: moniker-end

Zbudujemy rozwiązanie i projekt od podstaw jako ćwiczenie edukacyjne, aby zrozumieć koncepcję projektu. W ogólnym użyciu programu Visual Studio prawdopodobnie użyjesz niektórych szablonów różnych *projektów,* które oferuje program Visual Studio podczas tworzenia nowego projektu.

> [!NOTE]
> Rozwiązania i projekty nie są wymagane do tworzenia aplikacji w programie Visual Studio. Można również po prostu otworzyć folder, który zawiera kod i rozpocząć kodowanie, tworzenie i debugowanie. Na przykład jeśli sklonujesz repozytorium [GitHub,](https://github.com/) może nie zawierać projektów i rozwiązań programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Tworzenie kodu w programie Visual Studio bez projektów i rozwiązań.](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)

## <a name="solutions-and-projects"></a>Rozwiązania i projekty

Pomimo swojej nazwy, rozwiązanie nie jest "odpowiedzią". Rozwiązanie jest po prostu kontener używany przez program Visual Studio do organizowania jednego lub więcej powiązanych projektów. Po otwarciu rozwiązania w programie Visual Studio, automatycznie ładuje wszystkie projekty, które zawiera rozwiązanie.

### <a name="create-a-solution"></a>Tworzenie rozwiązania

Rozpoczniemy naszą eksplorację od stworzenia pustego rozwiązania. Po zapoznaniu się z programem Visual Studio prawdopodobnie nie znajdziesz się tworzenie pustych rozwiązań bardzo często. Podczas tworzenia nowego projektu visual studio automatycznie tworzy rozwiązanie do domu projektu, jeśli nie ma rozwiązania już otwarte.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

1. Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

   Zostanie otwarte okno dialogowe **Nowy projekt.**

1. W lewym okienku rozwiń węzeł **Inne typy projektów**, a następnie wybierz pozycję **Rozwiązania programu Visual Studio**. W środkowym okienku wybierz szablon **Puste rozwiązanie.** Nazwij rozwiązanie **QuickSolution**, a następnie wybierz przycisk **OK.**

   ![Pusty szablon rozwiązania w programie Visual Studio 2017](media/tutorial-projects-new-solution.png)

   Strona **początkowa** zostanie zamknięta, a rozwiązanie pojawi się w **Eksploratorze rozwiązań** po prawej stronie okna programu Visual Studio. Prawdopodobnie będziesz często używać **Eksploratora rozwiązań,** aby przeglądać zawartość projektów.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

3. Na stronie **Tworzenie nowego projektu** wprowadź puste **rozwiązanie** w polu wyszukiwania, zaznacz szablon **Puste rozwiązanie,** a następnie wybierz pozycję **Dalej**.

   ![Pusty szablon rozwiązania w programie Visual Studio 2019](media/vs-2019/tutorial-projects-blank-solution-template.png)

4. Nazwij rozwiązanie **QuickSolution**, a następnie wybierz pozycję **Utwórz**.

   Rozwiązanie pojawi się w **Eksploratorze rozwiązań** po prawej stronie okna programu Visual Studio. Prawdopodobnie będziesz często używać **Eksploratora rozwiązań,** aby przeglądać zawartość projektów.

::: moniker-end

### <a name="add-a-project"></a>Dodawanie projektu

Teraz dodajmy nasz pierwszy projekt do rozwiązania. Zaczniemy od pustego projektu i dodamy elementy, których potrzebujemy do projektu.

::: moniker range="vs-2017"

1. Z menu po kliknięciu prawym przyciskiem myszy lub menu kontekstowego **rozwiązania "QuickSolution"** w **Eksploratorze rozwiązań**wybierz pozycję **Dodaj** > **nowy projekt**.

   Zostanie otwarte okno dialogowe **Dodawanie nowego projektu.**

1. W lewym okienku rozwiń węzeł **Visual C#** i wybierz pozycję **Pulpit systemu Windows**. Następnie w środkowym okienku wybierz szablon **Pusty projekt (NET Framework).** Nazwij projekt **QuickDate**, a następnie wybierz **przycisk OK**.

   Projekt o nazwie QuickDate pojawia się pod rozwiązaniem w **Eksploratorze rozwiązań**. Obecnie zawiera jeden plik o nazwie *App.config*.

   > [!NOTE]
   > Jeśli nie widzisz **programu Visual C#** w lewym okienku okna dialogowego, należy zainstalować obciążenie programu Visual Studio **deweloperskie .NET dla deweloperów pulpitu.** Program Visual Studio używa instalacji opartej na obciążeniu, aby zainstalować tylko składniki potrzebne do typu programu dewelopera. Łatwym sposobem zainstalowania nowego obciążenia jest wybranie łącza **Instalatora programu Visual Studio** w lewym dolnym rogu okna dialogowego Dodawanie nowego **projektu.** Po uruchomieniu Instalatora programu Visual Studio wybierz obciążenie **programistyczne pulpitu .NET,** a następnie przycisk **Modyfikuj.**
   >
   > ![Otwórz łącze instalatora programu Visual Studio](media/tutorial-projects-open-installer.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Z menu po kliknięciu prawym przyciskiem myszy lub menu kontekstowego **rozwiązania "QuickSolution"** w **Eksploratorze rozwiązań**wybierz pozycję **Dodaj** > **nowy projekt**.

   Zostanie otwarte okno dialogowe **z napisem Dodaj nowy projekt**.

1. Wprowadź tekst **pusty** w polu wyszukiwania u góry, a następnie wybierz pozycję **C#** w obszarze **Język**.

1. Wybierz szablon **Pusty projekt (.NET Framework),** a następnie wybierz pozycję **Dalej**.

1. Nazwij projekt **QuickDate**, a następnie wybierz pozycję **Utwórz**.

   Projekt o nazwie QuickDate pojawia się pod rozwiązaniem w **Eksploratorze rozwiązań**. Obecnie zawiera jeden plik o nazwie *App.config*.

   > [!NOTE]
   > Jeśli nie widzisz szablonu **Pusty projekt (NET Framework),** musisz zainstalować obciążenie programu Visual Studio **dla deweloperów pulpitu platformy .NET.** Program Visual Studio używa instalacji opartej na obciążeniu, aby zainstalować tylko składniki potrzebne do typu programu dewelopera. Łatwym sposobem zainstalowania nowego obciążenia podczas tworzenia nowego projektu jest **wybranie** łącza Zainstaluj więcej narzędzi i funkcji pod tekstem, który mówi Nie znajdując **tego, czego szukasz?**. Po uruchomieniu Instalatora programu Visual Studio wybierz obciążenie **programistyczne pulpitu .NET,** a następnie przycisk **Modyfikuj.**
   >
   > ![Otwórz łącze instalatora programu Visual Studio](media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Dodawanie elementu do projektu

Mamy pusty projekt. Dodajmy plik kodu.

1. Z menu wyświetlanego prawym przyciskiem myszy lub menu kontekstowego projektu **QuickDate** w **Eksploratorze rozwiązań**wybierz polecenie **Dodaj** > **nowy element**.

   Zostanie otwarte okno dialogowe **Dodawanie nowego elementu.**

1. Rozwiń pozycję **Elementy języka Visual C#,** a następnie wybierz pozycję **Kod**. W środkowym okienku wybierz szablon elementu **klasy.** Nazwij **kalendarz**zajęć , a następnie wybierz przycisk **Dodaj.**

   Plik o nazwie *Calendar.cs* jest dodawany do projektu. *Cs* na końcu jest rozszerzeniem pliku, które jest podane do plików kodu C#. Plik pojawi się w wizualnej hierarchii projektu w **Eksploratorze rozwiązań,** a jego zawartość zostanie otwarta w edytorze.

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

   Nie musisz rozumieć, co robi kod, ale jeśli chcesz, możesz uruchomić program, naciskając **klawisz Ctrl**+**F5** i zobaczyć, że drukuje on dzisiejszą datę w oknie konsoli (lub standardowe wyjście).

## <a name="add-a-second-project"></a>Dodawanie drugiego projektu

Często rozwiązania zawierają więcej niż jeden projekt i często te projekty odwołują się do siebie. Niektóre projekty w rozwiązaniu mogą być bibliotekami klas, niektóre aplikacje wykonywalne, a niektóre mogą być projektami testów jednostkowych lub witrynami sieci Web.

Dodajmy projekt testu jednostkowego do naszego rozwiązania. Tym razem zaczniemy od szablonu projektu, więc nie musimy dodawać dodatkowego pliku kodu do projektu.

1. Z menu po kliknięciu prawym przyciskiem myszy lub menu kontekstowego **rozwiązania "QuickSolution"** w **Eksploratorze rozwiązań**wybierz pozycję **Dodaj** > **nowy projekt**.

::: moniker range="vs-2017"

2. W lewym okienku rozwiń **pozycję Visual C#** i wybierz kategorię **Test.** W środkowym okienku wybierz szablon projektu **projektu testu MSTest (net core).** Nazwij projekt **QuickTest**, a następnie wybierz **przycisk OK**.

   Drugi projekt zostanie dodany do **Eksploratora rozwiązań,** a plik o nazwie *UnitTest1.cs* zostanie otwarty w edytorze.

   ![Eksplorator rozwiązań programu Visual Studio z dwoma projektami](media/tutorial-projects-solution-explorer.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. W oknie **dialogowym Dodawanie nowego projektu** wprowadź **test jednostki** tekstowej w polu wyszukiwania u góry, a następnie wybierz pozycję **C#** w obszarze **Język**.

3. Wybierz szablon projektu **testu MSTest (.NET Core),** a następnie wybierz pozycję **Dalej**.

4. Nadaj nazwę **skróconemu**testowi projektu, a następnie wybierz pozycję **Utwórz**.

   Drugi projekt zostanie dodany do **Eksploratora rozwiązań,** a plik o nazwie *UnitTest1.cs* zostanie otwarty w edytorze.

   ![Eksplorator rozwiązań programu Visual Studio z dwoma projektami](media/vs-2019/tutorial-projects-solution-explorer.png)

::: moniker-end

## <a name="add-a-project-reference"></a>Dodawanie odwołania do projektu

Będziemy używać nowego projektu testu jednostkowego, aby przetestować naszą metodę w projekcie **QuickDate,** więc musimy dodać odwołanie do tego projektu. Spowoduje to utworzenie *zależności kompilacji* między dwoma projektami, co oznacza, że podczas tworzenia rozwiązania **QuickDate** jest tworzona przed **quicktest.**

1. Wybierz węzeł **Zależności** w projekcie **QuickTest,** a następnie z menu po kliknięciu prawym przyciskiem myszy lub w menu kontekstowym wybierz polecenie **Dodaj odwołanie**.

   Zostanie otwarte okno dialogowe **Menedżer odwołań.**

1. W lewym okienku rozwiń pozycję **Projekty** i wybierz pozycję **Rozwiązanie**. W środkowym okienku wybierz pole wyboru obok **pozycji QuickDate**, a następnie wybierz przycisk **OK**.

   Zostanie dodane odwołanie do projektu **QuickDate.**

   ![Visual Studio 2019 Solution Explorer z dokumentacją odwołania do projektu](media/vs-2019/tutorial-projects-solution-explorer-reference.png)

## <a name="add-test-code"></a>Dodaj kod testu

1. Teraz dodamy kod testu do pliku kodu testu języka C#. Zastąp zawartość *UnitTest1.cs* następującym kodem:

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

   Pod niektórymi kodami zobaczysz czerwoną faliwę. Naprawimy ten błąd, czyniąc projekt testowy [zestawem znajomych](/dotnet/standard/assembly/friend-assemblies) w projekcie **QuickDate.**

1. W projekcie **QuickDate** otwórz plik *Calendar.cs,* jeśli nie jest jeszcze otwarty. Dodaj następujące za <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> pomocą [instrukcji](/dotnet/csharp/language-reference/keywords/using-statement) i atrybutu w górnej części pliku, aby rozwiązać błąd w projekcie testowym.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Plik kodu powinien wyglądać następująco:

   ![Kod CSharp](media/tutorial-projects-cs-code.png)

## <a name="project-properties"></a>Właściwości projektu

Wiersz w pliku *Calendar.cs,* który zawiera <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut odwołuje się do nazwy zestawu (nazwa pliku) projektu **QuickTest.** Nazwa zestawu nie zawsze może być taka sama jak nazwa projektu. Aby znaleźć nazwę zestawu projektu, otwórz właściwości projektu.

1. W **Eksploratorze rozwiązań**wybierz projekt **QuickTest.** W menu prawym przyciskiem myszy lub w menu kontekstowym wybierz polecenie **Właściwości**lub po prostu naciśnij klawisz **Alt**+**Enter**.

   *Strony właściwości* projektu są otwierane na karcie **Aplikacja.** Strony właściwości zawierają różne ustawienia dla projektu. Należy zauważyć, że nazwa zestawu projektu **QuickTest** jest rzeczywiście "QuickTest". Jeśli chcesz to zmienić, to jest miejsce, w którym byś to zrobił. Następnie podczas tworzenia projektu testowego nazwa wynikowego pliku binarnego zmieni się z *quicktest.dll* na cokolwiek wybierzesz.

   ![Właściwości projektu](media/tutorial-projects-netcore-properties.png)

1. Zapoznaj się z niektórymi innymi kartami stron właściwości projektu, takich jak **Kompilacja** i **Debugowanie**. Te karty są różne dla różnych typów projektów.

## <a name="next-steps"></a>Następne kroki

Jeśli chcesz sprawdzić, czy test jednostkowy działa, wybierz polecenie**Uruchom** >  **test** > **wszystkie testy** z paska menu. Otworzy się okno o nazwie **Eksplorator testów** i powinien zostać wyświetlony, że **test TestGetCurrentDate** przebiega pomyślnie.

![Eksplorator testów w programie Visual Studio z pozytywnym testem](media/tutorial-projects-test-explorer.png)

::: moniker range="vs-2017"

> [!TIP]
> Jeśli **Eksplorator testów** nie otwiera się automatycznie, otwórz go, wybierając **pozycję Test** > **Eksploratora testów** **systemu Windows** > z paska menu.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Jeśli **Eksplorator testów** nie otwiera się automatycznie, otwórz go, **wybierając** > **eksploratora testów** z paska menu.

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Tworzenie projektów i rozwiązań](../ide/creating-solutions-and-projects.md)
- [Zarządzanie właściwościami projektów i rozwiązań](../ide/managing-project-and-solution-properties.md)
- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
- [Tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Omówienie ide programu Visual Studio](../get-started/visual-studio-ide.md)
