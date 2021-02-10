---
title: Projekty samouczków i rozwiązania Visual Basic
description: Dowiedz się, jak utworzyć rozwiązanie i projekt w programie Visual Studio jako deweloper Visual Basic.
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
ms.openlocfilehash: 36aabdd07dd7fa966a31d8fc3844e68d816c59ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944527"
---
# <a name="learn-about-projects-and-solutions-using-visual-basic"></a>Poznaj projekty i rozwiązania przy użyciu Visual Basic

W tym artykule wprowadzającym zapoznajemy znaczenie tworzenia *rozwiązania* i *projektu* w programie Visual Studio. Rozwiązanie jest kontenerem, który służy do organizowania jednego lub więcej powiązanych projektów kodu, na przykład projektu biblioteki klas i odpowiedniego projektu testowego. Zobaczymy właściwości projektu i niektóre z plików, które może zawierać. Utworzymy również odwołanie z jednego projektu do innego.

::: moniker range="vs-2017"

> [!TIP]
> Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

Utworzymy rozwiązanie i projekt od podstaw jako ćwiczenie edukacyjne, aby zrozumieć koncepcję projektu. W ogólnym użyciu programu Visual Studio prawdopodobnie będziesz używać niektórych różnych *szablonów* projektów oferowanych przez program Visual Studio podczas tworzenia nowego projektu.

> [!NOTE]
> Rozwiązania i projekty nie są wymagane do tworzenia aplikacji w programie Visual Studio. Możesz również otworzyć folder, który zawiera kod i rozpocząć kodowanie, kompilowanie i debugowanie. Na przykład w przypadku klonowania repozytorium [GitHub](https://github.com/) może nie zawierać projektów i rozwiązań programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Programowanie kodu w programie Visual Studio bez projektów i rozwiązań](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Rozwiązania i projekty

Pomimo nazwy, rozwiązanie nie jest "odpowiedzią". Rozwiązanie to po prostu kontener używany przez program Visual Studio do organizowania jednego lub kilku powiązanych projektów. Po otwarciu rozwiązania w programie Visual Studio program automatycznie ładuje wszystkie projekty, które zawiera rozwiązanie.

### <a name="create-a-solution"></a>Tworzenie rozwiązania

Rozpocznie nasze eksplorację, tworząc puste rozwiązanie. Po uzyskaniu informacji o programie Visual Studio prawdopodobnie nie będzie można często tworzyć puste rozwiązania. Podczas tworzenia nowego projektu program Visual Studio automatycznie tworzy rozwiązanie do przechowywania projektu, jeśli nie jest już otwarte rozwiązanie.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

1. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt**.

   Zostanie otwarte okno dialogowe **Nowy projekt** .

1. W okienku po lewej stronie rozwiń pozycję **Inne typy projektów**, a następnie wybierz pozycję **rozwiązania programu Visual Studio**. W środkowym okienku wybierz szablon **pustego rozwiązania** . Nazwij rozwiązanie **QuickSolution**, a następnie wybierz przycisk **OK**.

   ![Pusty szablon rozwiązania w programie Visual Studio](../media/tutorial-projects-new-solution.png)

   **Strona początkowa** zostanie ZAMKNIĘTA, a rozwiązanie pojawia się w **Eksplorator rozwiązań** po prawej stronie okna programu Visual Studio. Prawdopodobnie będziesz używać **Eksplorator rozwiązań** często, aby przeglądać zawartość Twoich projektów.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

3. Na stronie **Tworzenie nowego projektu** wprowadź **puste rozwiązanie** w polu wyszukiwania, wybierz szablon **pustego rozwiązania** , a następnie wybierz przycisk **dalej**.

   ![Pusty szablon rozwiązania w programie Visual Studio 2019](../media/vs-2019/tutorial-projects-blank-solution-template.png)

4. Nazwij rozwiązanie **QuickSolution**, a następnie wybierz pozycję **Utwórz**.

   Rozwiązanie pojawia się w **Eksplorator rozwiązań** po prawej stronie okna programu Visual Studio. Prawdopodobnie będziesz używać **Eksplorator rozwiązań** często, aby przeglądać zawartość Twoich projektów.

::: moniker-end

### <a name="add-a-project"></a>Dodaj projekt

Teraz Dodajmy nasz pierwszy projekt do rozwiązania. Zaczniemy od pustego projektu i dodamy elementy, których potrzebujemy do projektu.

::: moniker range="vs-2017"

1. W obszarze **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy lub menu kontekstowe **rozwiązania "QuickSolution"** , wybierz polecenie **Dodaj** > **Nowy projekt**.

   Zostanie otwarte okno dialogowe **Dodaj nowy projekt** .

1. W lewym okienku rozwiń węzeł **Visual Basic** i wybierz pozycję **Windows Desktop**. Następnie w środkowym okienku wybierz szablon **pusty projekt (.NET Framework)** . Nazwij projekt **QuickDate**, a następnie wybierz przycisk **OK** .

   Projekt o nazwie QuickDate pojawia się poniżej rozwiązania w **Eksplorator rozwiązań**. Obecnie zawiera pojedynczy plik o nazwie *App.config*.

   > [!NOTE]
   > Jeśli nie widzisz **Visual Basic** w lewym okienku okna dialogowego, należy zainstalować program **.NET Desktop Development** w programie *Visual Studio.* Program Visual Studio używa instalacji opartej na obciążeniach, aby zainstalować tylko te składniki, które są potrzebne dla danego typu rozwoju. Łatwym sposobem instalacji nowego obciążenia jest wybranie linku **otwórz Instalator programu Visual Studio** w lewym dolnym rogu okna dialogowego **Dodawanie nowego projektu** . Po uruchomieniu Instalator programu Visual Studio wybierz obciążenie **Programowanie aplikacji klasycznych platformy .NET** , a następnie przycisk **Modyfikuj** .
   >
   > ![Otwórz link Instalator programu Visual Studio](media/tutorial-projects-open-installer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. W obszarze **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy lub menu kontekstowe **rozwiązania "QuickSolution"** , wybierz polecenie **Dodaj** > **Nowy projekt**.

   Zostanie otwarte okno dialogowe z komunikatem **Dodawanie nowego projektu**.

1. Wprowadź **pusty** tekst w polu wyszukiwania u góry, a następnie wybierz **Visual Basic** w obszarze **Język**.

1. Wybierz szablon **pustego projektu (.NET Framework)** , a następnie wybierz przycisk **dalej**.

1. Nazwij projekt **QuickDate**, a następnie wybierz pozycję **Utwórz**.

   Projekt o nazwie QuickDate pojawia się poniżej rozwiązania w **Eksplorator rozwiązań**. Obecnie zawiera pojedynczy plik o nazwie *App.config*.

   > [!NOTE]
   > Jeśli nie widzisz szablonu **pustego projektu (.NET Framework)** , musisz zainstalować **środowisko deweloperskie programu .NET Desktop** *.* Program Visual Studio używa instalacji opartej na obciążeniach, aby zainstalować tylko te składniki, które są potrzebne dla danego typu rozwoju. Prostym sposobem na zainstalowanie nowego obciążenia podczas tworzenia nowego projektu jest wybranie linku **Zainstaluj więcej narzędzi i funkcji** pod tekstem, który **nie jest szukany?**. Po uruchomieniu Instalator programu Visual Studio wybierz obciążenie **Programowanie aplikacji klasycznych platformy .NET** , a następnie przycisk **Modyfikuj** .
   >
   > ![Link Instalatora w programie Visual Studio 2019](../media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Dodaj element do projektu

Mamy pusty projekt. Dodajmy plik kodu.

1. Z menu podręcznego kliknij lub kontekstowego projektu **QuickDate** w **Eksplorator rozwiązań** wybierz pozycję **Dodaj**  >  **nowy element**.

   Zostanie otwarte okno dialogowe **Dodaj nowy element** .

1. Rozwiń węzeł **wspólne elementy**, a następnie wybierz pozycję **kod**. W środkowym okienku wybierz szablon element **klasy** . Nazwij **Kalendarz** klasy, a następnie wybierz przycisk **Dodaj** .

   Plik o nazwie *Calendar. vb* został dodany do projektu. *. Vb* na końcu to rozszerzenie pliku, które ma Visual Basic plików kodu. Plik jest wyświetlany w hierarchii projektu wizualizacji w **Eksplorator rozwiązań** i jego zawartość jest otwarta w edytorze.

1. Zastąp zawartość pliku *Calendar. vb* następującym kodem:

   ```vb
   Class Calendar
       Public Shared Function GetCurrentDate() As Date
           Return DateTime.Now.Date
       End Function
   End Class
   ```

   `Calendar`Klasa zawiera pojedynczą funkcję, `GetCurrentDate` która zwraca bieżącą datę.

1. Otwórz właściwości projektu, klikając dwukrotnie **mój projekt** w **Eksplorator rozwiązań**. Na karcie **aplikacja** Zmień **Typ aplikacji** na **Biblioteka klas**. Ten krok jest niezbędny do pomyślnego skompilowania projektu.

1. Skompiluj projekt, klikając prawym przyciskiem myszy pozycję **QuickDate** w **Eksplorator rozwiązań** i wybierając pozycję **Kompiluj**. W oknie **danych wyjściowych** powinien zostać wyświetlony komunikat pomyślne skompilowanie.

## <a name="add-a-second-project"></a>Dodaj drugi projekt

Rozwiązanie to często dotyczy rozwiązań zawierających więcej niż jeden projekt i często te projekty odwołują się do siebie. Niektóre projekty w rozwiązaniu mogą być bibliotekami klas, niektóre aplikacje wykonywalne i niektóre mogą być projektami testów jednostkowych lub witrynami sieci Web.

Dodajmy projekt testu jednostkowego do naszego rozwiązania. Tym razem zaczniemy od szablonu projektu, więc nie trzeba dodawać dodatkowego pliku kodu do projektu.

1. W obszarze **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy lub menu kontekstowe **rozwiązania "QuickSolution"** , wybierz polecenie **Dodaj**  >  **Nowy projekt**.

::: moniker range="Vs-2017"

2. W lewym okienku rozwiń węzeł **Visual Basic** i wybierz kategorię **test** . W środkowym okienku wybierz szablon projektu **test jednostkowy projektu (.NET Framework)** . Nazwij projekt **Quicktest**, a następnie wybierz przycisk **OK**.

   Drugi projekt zostanie dodany do **Eksplorator rozwiązań**, a plik o nazwie *UnitTest1. vb* zostanie otwarty w edytorze.

   ![Program Visual Studio Eksplorator rozwiązań z dwoma projektami](media/tutorial-projects-solution-explorer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. W oknie dialogowym **Dodawanie nowego projektu** wprowadź **test jednostkowy** tekstu w polu wyszukiwania u góry, a następnie wybierz **Visual Basic** w obszarze **Język**.

3. Wybierz szablon projektu **test jednostkowy (.NET Framework)** , a następnie wybierz przycisk **dalej**.

4. Nazwij projekt **Quicktest**, a następnie wybierz pozycję **Utwórz**.

   Drugi projekt zostanie dodany do **Eksplorator rozwiązań**, a plik o nazwie *UnitTest1. vb* zostanie otwarty w edytorze.

::: moniker-end

## <a name="add-a-project-reference"></a>Dodaj odwołanie do projektu

Będziemy używać nowego projektu testów jednostkowych do testowania naszej metody w projekcie **QuickDate** , więc musimy dodać odwołanie do tego projektu. Powoduje to utworzenie *zależności kompilacji* między dwoma projektami, co oznacza, że podczas kompilowania rozwiązania **QuickDate** jest tworzona przed **Quicktest**.

1. Wybierz węzeł **odwołania** w projekcie **Quicktest** i z menu kontekstowego kliknij prawym przyciskiem myszy lub wybierz polecenie **Dodaj odwołanie**.

   ![Dodaj menu odwołania](media/tutorial-projects-add-reference-vb.png)

   Zostanie otwarte okno dialogowe **Menedżer odwołań** .

1. W lewym okienku rozwiń węzeł **projekty** i wybierz pozycję **rozwiązanie**. W środkowym okienku zaznacz pole wyboru obok pozycji **QuickDate**, a następnie wybierz przycisk **OK** .

   Dodano odwołanie do projektu **QuickDate** .

## <a name="add-test-code"></a>Dodaj kod testu

1. Teraz dodamy kod testowy do pliku kodu Visual Basic. Zastąp zawartość *UnitTest1. vb* poniższym kodem.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(Date.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   Zobaczysz czerwoną część kodu. Naprawimy ten błąd przez utworzenie projektu testowego jako [przyjaciela](/dotnet/visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies) do projektu **QuickDate** .

1. W projekcie **QuickDate** Otwórz plik *Calendar. vb* , jeśli nie jest jeszcze otwarty, i Dodaj następującą [instrukcję Imports](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) i <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut, aby rozwiązać błąd w projekcie testowym.

   ```vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("QuickTest")>
   ```

   Plik kodu powinien wyglądać następująco:

   ![Kod Visual Basic](media/tutorial-projects-code-vb.png)

## <a name="project-properties"></a>Właściwości projektu

Wiersz w pliku *Calendar. vb* , który zawiera <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut odwołuje się do nazwy zestawu (nazwa pliku) projektu **Quicktest** . Nazwa zestawu może nie zawsze być taka sama jak nazwa projektu. Aby znaleźć nazwę zestawu projektu, Otwórz właściwości projektu.

1. W **Eksplorator rozwiązań** wybierz projekt **Quicktest** . W menu kontekstowym lub prawym przyciskiem myszy wybierz pozycję **Właściwości** lub po prostu naciśnij klawisz **Alt** + **Enter**. (Możesz również kliknąć dwukrotnie pozycję **mój projekt** w **Eksplorator rozwiązań**).

   *Strony właściwości* projektu otwartego na karcie **aplikacja** . Strony właściwości zawierają różne ustawienia dla projektu. Należy zauważyć, że nazwa zestawu projektu **Quicktest** jest rzeczywiście "Quicktest". Jeśli chcesz ją zmienić, możesz to zrobić. Następnie podczas budowania projektu testowego nazwa pliku binarnego, który zostanie zmieniony, zmieni się z *QuickTest.dll* na dowolnie wybrany.

   ![Właściwości projektu](../media/tutorial-projects-properties.png)

1. Zapoznaj się z innymi kartami stron właściwości projektu, takimi jak **kompilacja** i **Ustawienia**. Te karty są różne dla różnych typów projektów.

## <a name="optional-run-the-test"></a>Obowiązkowe Uruchom test

Jeśli chcesz sprawdzić, czy test jednostkowy działa, wybierz pozycję **Testuj**  >  **Uruchom**  >  **wszystkie testy** z paska menu. Zostanie otwarte okno o nazwie **Eksplorator testów** i zobaczysz, że test **TestGetCurrentDate** kończy się powodzeniem.

![Eksplorator tekstów w programie Visual Studio pokazujący zakończony test](../media/tutorial-projects-test-explorer.png)

> [!TIP]
> Jeśli **Eksplorator testów** nie zostanie otwarty automatycznie, otwórz go, wybierając pozycję **Testuj**  >    >  **Eksplorator testów** systemu Windows na pasku menu.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej na temat programu Visual Studio, należy rozważyć utworzenie aplikacji, postępując zgodnie z jednym z [samouczków Visual Basic](index.yml).

## <a name="see-also"></a>Zobacz też

- [Tworzenie projektów i rozwiązań](../../ide/creating-solutions-and-projects.md)
- [Zarządzanie właściwościami projektów i rozwiązań](../../ide/managing-project-and-solution-properties.md)
- [Zarządzanie odwołaniami w projekcie](../../ide/managing-references-in-a-project.md)
- [Tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Środowisko IDE programu Visual Studio — omówienie](../../get-started/visual-studio-ide.md)
