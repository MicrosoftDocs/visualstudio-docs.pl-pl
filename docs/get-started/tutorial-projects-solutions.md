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
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579975"
---
# <a name="learn-about-projects-and-solutions"></a>Dowiedz się więcej o projekty i rozwiązania

W tym artykule wprowadzającym zapoznajemy znaczenie tworzenia *rozwiązania* i *projektu* w programie Visual Studio. Rozwiązanie jest kontenerem, który służy do organizowania jednego lub więcej powiązanych projektów kodu, na przykład projektu biblioteki klas i odpowiedniego projektu testowego. Omówimy właściwości projektu i niektórych plików, który może zawierać. Również utworzymy odwołanie z jednego projektu do drugiego.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

Firma Microsoft będzie konstruowania rozwiązania i projektu od podstaw w charakterze edukacyjnym ćwiczenia zrozumienie pojęcia projektu. W ogólnym użyciu programu Visual Studio prawdopodobnie będziesz używać niektórych różnych *szablonów* projektów oferowanych przez program Visual Studio podczas tworzenia nowego projektu.

> [!NOTE]
> Rozwiązania i projekty nie są wymagane do tworzenia aplikacji w programie Visual Studio. Możesz też po prostu otwórz folder, który zawiera kod i uruchamiania kodowania, kompilowania i debugowania. Na przykład w przypadku klonowania repozytorium [GitHub](https://github.com/) może nie zawierać projektów i rozwiązań programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Programowanie kodu w programie Visual Studio bez projektów i rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Rozwiązania i projekty

Pomimo nazwy, rozwiązanie nie jest "odpowiedzią". Rozwiązanie to po prostu kontener używany przez program Visual Studio do organizowania jednego lub kilku powiązanych projektów. Po otwarciu rozwiązania w programie Visual Studio program automatycznie ładuje wszystkie projekty, które zawiera rozwiązanie.

### <a name="create-a-solution"></a>Tworzenie rozwiązania

Rozpoczniemy naszych badań, tworząc puste rozwiązanie. Po uzyskaniu znasz programu Visual Studio, prawdopodobnie nie będzie zaczniesz tworzyć puste rozwiązania bardzo często. Podczas tworzenia nowego projektu programu Visual Studio automatycznie tworzy rozwiązanie do przechowywania projektu, jeśli nie ma rozwiązania już otwarte.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

1. Na górnym pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

   Zostanie otwarte okno dialogowe **Nowy projekt** .

1. W okienku po lewej stronie rozwiń pozycję **Inne typy projektów**, a następnie wybierz pozycję **rozwiązania programu Visual Studio**. W środkowym okienku wybierz szablon **pustego rozwiązania** . Nazwij rozwiązanie **QuickSolution**, a następnie wybierz przycisk **OK** .

   ![Pusty szablon rozwiązania w programie Visual Studio 2017](media/tutorial-projects-new-solution.png)

   **Strona początkowa** zostanie ZAMKNIĘTA, a rozwiązanie pojawia się w **Eksplorator rozwiązań** po prawej stronie okna programu Visual Studio. Prawdopodobnie będziesz używać **Eksplorator rozwiązań** często, aby przeglądać zawartość Twoich projektów.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

3. Na stronie **Tworzenie nowego projektu** wprowadź **puste rozwiązanie** w polu wyszukiwania, wybierz szablon **pustego rozwiązania** , a następnie wybierz przycisk **dalej**.

   ![Pusty szablon rozwiązania w programie Visual Studio 2019](media/vs-2019/tutorial-projects-blank-solution-template.png)

4. Nazwij rozwiązanie **QuickSolution**, a następnie wybierz pozycję **Utwórz**.

   Rozwiązanie pojawia się w **Eksplorator rozwiązań** po prawej stronie okna programu Visual Studio. Prawdopodobnie będziesz używać **Eksplorator rozwiązań** często, aby przeglądać zawartość Twoich projektów.

::: moniker-end

### <a name="add-a-project"></a>Dodaj projekt

Teraz Dodajmy nasz pierwszy projekt do rozwiązania. Firma Microsoft będzie rozpoczynać pusty projekt i dodać elementy, które należy do projektu.

::: moniker range="vs-2017"

1. W obszarze **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy lub menu kontekstowe **rozwiązania "QuickSolution"** , wybierz **Dodaj** > **Nowy projekt**.

   Zostanie otwarte okno dialogowe **Dodaj nowy projekt** .

1. W okienku po lewej stronie rozwiń **pozycję C# Wizualizacja** i wybierz pozycję **Windows Desktop**. Następnie w środkowym okienku wybierz szablon **pusty projekt (.NET Framework)** . Nazwij projekt **QuickDate**, a następnie wybierz przycisk **OK**.

   Projekt o nazwie QuickDate pojawia się poniżej rozwiązania w **Eksplorator rozwiązań**. Obecnie zawiera pojedynczy plik o nazwie *App. config*.

   > [!NOTE]
   > Jeśli **Wizualizacja C#**  nie jest widoczna w lewym okienku okna dialogowego, należy zainstalować program **.NET Desktop Development** w programie Visual Studio. Program Visual Studio używa instalacji opartej na obciążeniach, aby zainstalować tylko składniki potrzebne do tego typu rozwoju. Łatwym sposobem instalacji nowego obciążenia jest wybranie linku **otwórz Instalator programu Visual Studio** w lewym dolnym rogu okna dialogowego **Dodawanie nowego projektu** . Po uruchomieniu Instalator programu Visual Studio wybierz obciążenie **Programowanie aplikacji klasycznych platformy .NET** , a następnie przycisk **Modyfikuj** .
   >
   > ![Otwórz łącze w Instalatorze programu Visual Studio](media/tutorial-projects-open-installer.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. W obszarze **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy lub menu kontekstowe **rozwiązania "QuickSolution"** , wybierz **Dodaj** > **Nowy projekt**.

   Zostanie otwarte okno dialogowe z komunikatem **Dodawanie nowego projektu**.

1. Wprowadź **pusty** tekst w polu wyszukiwania u góry, a następnie wybierz pozycję **C#** w obszarze **Język**.

1. Wybierz szablon **pustego projektu (.NET Framework)** , a następnie wybierz przycisk **dalej**.

1. Nazwij projekt **QuickDate**, a następnie wybierz pozycję **Utwórz**.

   Projekt o nazwie QuickDate pojawia się poniżej rozwiązania w **Eksplorator rozwiązań**. Obecnie zawiera pojedynczy plik o nazwie *App. config*.

   > [!NOTE]
   > Jeśli nie widzisz szablonu **pustego projektu (.NET Framework)** , musisz zainstalować program **.NET Desktop Development** w programie Visual Studio. Program Visual Studio używa instalacji opartej na obciążeniach, aby zainstalować tylko składniki potrzebne do tego typu rozwoju. Prostym sposobem na zainstalowanie nowego obciążenia podczas tworzenia nowego projektu jest wybranie linku **Zainstaluj więcej narzędzi i funkcji** pod tekstem, który **nie jest szukany?** . Po uruchomieniu Instalator programu Visual Studio wybierz obciążenie **Programowanie aplikacji klasycznych platformy .NET** , a następnie przycisk **Modyfikuj** .
   >
   > ![Otwórz łącze w Instalatorze programu Visual Studio](media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Dodaj element do projektu

Mamy pusty projekt. Dodajmy pliku kodu.

1. Z menu podręcznego kliknij lub kontekstowego projektu **QuickDate** w **Eksplorator rozwiązań**wybierz pozycję **Dodaj** > **nowy element**.

   Zostanie otwarte okno dialogowe **Dodaj nowy element** .

1. Rozwiń **element C# Visual Items**, a następnie wybierz pozycję **Code (kod**). W środkowym okienku wybierz szablon element **klasy** . Nazwij **Kalendarz**klasy, a następnie wybierz przycisk **Dodaj** .

   Plik o nazwie *Calendar.cs* jest dodawany do projektu. *. Cs* na końcu to rozszerzenie pliku, które jest określone dla C# plików kodu. Plik jest wyświetlany w hierarchii projektu wizualizacji w **Eksplorator rozwiązań**, a jego zawartość jest otwierana w edytorze.

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

   Nie musisz zrozumieć, co robi kod, ale jeśli chcesz, możesz uruchomić program, naciskając klawisz **Ctrl**+**F5** i sprawdź, czy w oknie konsoli (lub w standardowym wyjściu) jest drukowana dzisiejsza data.

## <a name="add-a-second-project"></a>Dodasz drugi projekt

Jest typowe dla rozwiązań wzajemnie się zawierały więcej niż jeden projekt, a także często tych odwołań projektów. Niektóre projekty w rozwiązaniu może być bibliotek klas, niektóre pliku wykonywalnego aplikacji i może spowodować projektów testów jednostkowych lub witryn sieci Web.

Dodajmy projektu testu jednostkowego do naszego rozwiązania. Teraz Zaczniemy z szablonu projektu, nie mamy dodać plik dodatkowego kodu do projektu.

1. W obszarze **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy lub menu kontekstowe **rozwiązania "QuickSolution"** , wybierz **Dodaj** > **Nowy projekt**.

::: moniker range="vs-2017"

2. W okienku po lewej stronie rozwiń **pozycję C# Wizualizacja** i wybierz kategorię **test** . W środkowym okienku wybierz szablon projektu **projektu testowego MSTest (.NET Core)** . Nazwij projekt **Quicktest**, a następnie wybierz przycisk **OK**.

   Drugi projekt zostanie dodany do **Eksplorator rozwiązań**, a w edytorze zostanie otwarty plik o nazwie *UnitTest1.cs* .

   ![Eksploratorze rozwiązań Visual Studio za pomocą dwóch projektów](media/tutorial-projects-solution-explorer.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. W oknie dialogowym **Dodawanie nowego projektu** wprowadź **test jednostkowy** tekstu w polu wyszukiwania u góry, a następnie wybierz pozycję **C#** w obszarze **Język**.

3. Wybierz szablon projektu **projektu testowego MSTest (.NET Core)** , a następnie wybierz przycisk **dalej**.

4. Nazwij projekt **Quicktest**, a następnie wybierz pozycję **Utwórz**.

   Drugi projekt zostanie dodany do **Eksplorator rozwiązań**, a w edytorze zostanie otwarty plik o nazwie *UnitTest1.cs* .

   ![Eksploratorze rozwiązań Visual Studio za pomocą dwóch projektów](media/vs-2019/tutorial-projects-solution-explorer.png)

::: moniker-end

## <a name="add-a-project-reference"></a>Dodaj odwołanie do projektu

Będziemy używać nowego projektu testów jednostkowych do testowania naszej metody w projekcie **QuickDate** , więc musimy dodać odwołanie do tego projektu. Powoduje to utworzenie *zależności kompilacji* między dwoma projektami, co oznacza, że podczas kompilowania rozwiązania **QuickDate** jest tworzona przed **Quicktest**.

1. Wybierz węzeł **zależności** w projekcie **Quicktest** i z menu kontekstowego kliknij prawym przyciskiem myszy lub wybierz polecenie **Dodaj odwołanie**.

   Zostanie otwarte okno dialogowe **Menedżer odwołań** .

1. W lewym okienku rozwiń węzeł **projekty** i wybierz pozycję **rozwiązanie**. W środkowym okienku zaznacz pole wyboru obok pozycji **QuickDate**, a następnie wybierz przycisk **OK**.

   Dodano odwołanie do projektu **QuickDate** .

   ![Program Visual Studio 2019 Eksplorator rozwiązań pokazujący odwołanie do projektu](media/vs-2019/tutorial-projects-solution-explorer-reference.png)

## <a name="add-test-code"></a>Dodaj kod testowy

1. Teraz dodamy kod testowy do pliku kodu C# testu. Zastąp zawartość *UnitTest1.cs* następującym kodem:

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

   Zobaczysz czerwoną część kodu. Naprawimy ten błąd przez utworzenie projektu testowego jako [przyjaciela](/dotnet/standard/assembly/friend-assemblies) do projektu **QuickDate** .

1. W projekcie **QuickDate** otwórz plik *Calendar.cs* , jeśli nie jest jeszcze otwarty. Dodaj następującą [instrukcję using](/dotnet/csharp/language-reference/keywords/using-statement) i atrybut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> na początku pliku, aby rozwiązać błąd w projekcie testowym.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Plik kodu powinna wyglądać następująco:

   ![Kod języka CSharp](media/tutorial-projects-cs-code.png)

## <a name="project-properties"></a>Właściwości projektu

Wiersz w pliku *Calendar.cs* , który zawiera atrybut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> odwołuje się do nazwy zestawu (nazwa pliku) projektu **Quicktest** . Nazwa zestawu może nie być taka sama jak nazwa projektu. Aby znaleźć nazwy zestawu projektu, otwórz właściwości projektu.

1. W **Eksplorator rozwiązań**wybierz projekt **Quicktest** . Z menu kontekstowego kliknij prawym przyciskiem myszy lub wybierz polecenie **Właściwości**lub po prostu naciśnij klawisz **Alt**+**Enter**.

   *Strony właściwości* projektu otwartego na karcie **aplikacja** . Strony właściwości zawierają różne ustawienia dla projektu. Należy zauważyć, że nazwa zestawu projektu **Quicktest** jest rzeczywiście "Quicktest". Jeśli chcesz je zmienić, oznacza to, gdzie sposób, jak. Następnie podczas kompilowania projektu testowego nazwa pliku binarnego, który zostanie zmieniony z *Quicktest. dll* , będzie zmieniana z dowolnie wybranego.

   ![Właściwości projektu](media/tutorial-projects-netcore-properties.png)

1. Zapoznaj się z innymi kartami stron właściwości projektu, takimi jak **kompilacja** i **debugowanie**. Te karty są różne dla różnych typów projektów.

## <a name="next-steps"></a>Następne kroki

Jeśli chcesz sprawdzić, czy test jednostkowy działa, wybierz pozycję **testuj** > **Uruchom** > **wszystkie testy** z paska menu. Zostanie otwarte okno o nazwie **Eksplorator testów** i zobaczysz, że test **TestGetCurrentDate** kończy się powodzeniem.

![Eksplorator testów w Visual Studio przedstawiający przekazywane testu](media/tutorial-projects-test-explorer.png)

::: moniker range="vs-2017"

> [!TIP]
> Jeśli **Eksplorator testów** nie zostanie otwarty automatycznie, otwórz go, wybierając pozycję **testuj** > **Windows** > **Eksploratorze testów** z paska menu.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Jeśli **Eksplorator testów** nie zostanie otwarty automatycznie, otwórz go, wybierając **test** > test **Explorer** z paska menu.

::: moniker-end

## <a name="see-also"></a>Zobacz też

- [Tworzenie projektów i rozwiązań](../ide/creating-solutions-and-projects.md)
- [Zarządzanie właściwościami projektów i rozwiązań](../ide/managing-project-and-solution-properties.md)
- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
- [Tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Środowisko IDE programu Visual Studio — omówienie](../get-started/visual-studio-ide.md)
