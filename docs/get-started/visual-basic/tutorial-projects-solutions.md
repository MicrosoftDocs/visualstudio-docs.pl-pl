---
title: Projekty samouczków i rozwiązania Visual Basic
ms.date: 12/12/2018
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 48b3f2c9aae099e3ae5f2cf2d8c438fb0f9062a2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590218"
---
# <a name="learn-about-projects-and-solutions-using-visual-basic"></a>Poznaj projekty i rozwiązania przy użyciu Visual Basic

W tym artykule wprowadzające przedstawimy wyjaśniono tworzenie *rozwiązania* i *projektu* w programie Visual Studio. Rozwiązanie jest kontenerem, który służy do organizowania jednego lub więcej powiązanych projektów kodu, na przykład projektu biblioteki klas i odpowiedniego projektu testowego. Omówimy właściwości projektu i niektórych plików, który może zawierać. Również utworzymy odwołanie z jednego projektu do drugiego.

::: moniker range="vs-2017"

> [!TIP]
> Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads) strony, aby zainstalować go za darmo.

::: moniker-end

Firma Microsoft będzie konstruowania rozwiązania i projektu od podstaw w charakterze edukacyjnym ćwiczenia zrozumienie pojęcia projektu. Ogólne korzystający z programu Visual Studio, prawdopodobnie użyjesz niektóre z projektu różne *szablony* , program Visual Studio oferuje podczas tworzenia nowego projektu.

> [!NOTE]
> Rozwiązania i projekty nie są wymagane do tworzenia aplikacji w programie Visual Studio. Możesz też po prostu otwórz folder, który zawiera kod i uruchamiania kodowania, kompilowania i debugowania. Na przykład, jeśli można sklonować [GitHub](https://github.com/) repozytorium, może nie zawierać projektów programu Visual Studio i rozwiązania. Aby uzyskać więcej informacji, zobacz [tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Rozwiązania i projekty

Pomimo nazwy, rozwiązanie nie jest "odpowiedzią". Rozwiązanie to po prostu kontener używany przez program Visual Studio do organizowania jednego lub kilku powiązanych projektów. Po otwarciu rozwiązania w programie Visual Studio program automatycznie ładuje wszystkie projekty, które zawiera rozwiązanie.

### <a name="create-a-solution"></a>Tworzenie rozwiązania

Rozpoczniemy naszych badań, tworząc puste rozwiązanie. Po uzyskaniu znasz programu Visual Studio, prawdopodobnie nie będzie zaczniesz tworzyć puste rozwiązania bardzo często. Podczas tworzenia nowego projektu programu Visual Studio automatycznie tworzy rozwiązanie do przechowywania projektu, jeśli nie ma rozwiązania już otwarte.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

1. Na pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

   **Nowy projekt** zostanie otwarte okno dialogowe.

1. W okienku po lewej stronie rozwiń **inne typy projektów**, następnie wybierz **Visual Studio Solutions**. W środkowym okienku wybierz **puste rozwiązanie** szablonu. Nazwij rozwiązanie **QuickSolution**, a następnie wybierz przycisk **OK**.

   ![Pusty szablon rozwiązania w programie Visual Studio](../media/tutorial-projects-new-solution.png)

   **Strona startowa** zostanie zamknięty i rozwiązania zostaną wyświetlone w **Eksploratora rozwiązań** po prawej stronie okna programu Visual Studio. Prawdopodobnie użyjesz **Eksploratora rozwiązań** często, aby przeglądać zawartość Twoich projektów.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

3. Na stronie **Tworzenie nowego projektu** wprowadź **puste rozwiązanie** w polu wyszukiwania, wybierz szablon **pustego rozwiązania** , a następnie wybierz przycisk **dalej**.

   ![Pusty szablon rozwiązania w programie Visual Studio 2019](../media/vs-2019/tutorial-projects-blank-solution-template.png)

4. Nazwij rozwiązanie **QuickSolution**, a następnie wybierz pozycję **Utwórz**.

   Rozwiązanie pojawia się w **Eksplorator rozwiązań** po prawej stronie okna programu Visual Studio. Prawdopodobnie użyjesz **Eksploratora rozwiązań** często, aby przeglądać zawartość Twoich projektów.

::: moniker-end

### <a name="add-a-project"></a>Dodaj projekt

Teraz Dodajmy nasz pierwszy projekt do rozwiązania. Firma Microsoft będzie rozpoczynać pusty projekt i dodać elementy, które należy do projektu.

::: moniker range="vs-2017"

1. W obszarze **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy lub menu kontekstowe **rozwiązania "QuickSolution"** , wybierz **Dodaj** > **Nowy projekt**.

   **Dodaj nowy projekt** zostanie otwarte okno dialogowe.

1. W lewym okienku rozwiń węzeł **Visual Basic** i wybierz pozycję **Windows Desktop**. Następnie w środkowym okienku wybierz **pusty projekt (.NET Framework)** szablonu. Nadaj projektowi nazwę **QuickDate**, następnie wybierz **OK** przycisku.

   Projekt o nazwie QuickDate wyświetlany pod rozwiązania w **Eksploratora rozwiązań**. Obecnie zawiera jednego pliku o nazwie *App.config*.

   > [!NOTE]
   > Jeśli nie widzisz **Visual Basic** w lewym okienku okna dialogowego, należy zainstalować program **.NET Desktop Development** w programie *Visual Studio.* Visual Studio używa Instalacja oparta na obciążenie można instalować tylko składniki potrzebne do typ pracy deweloperskiej, co możesz zrobić. Prosty sposób, aby zainstalować nowe obciążenie jest wybranie **Otwórz Instalator programu Visual Studio** łącze w lewym dolnym rogu **Dodaj nowy projekt** okno dialogowe. Po uruchomieniu Instalatora programu Visual Studio wybierz **programowanie aplikacji klasycznych dla platformy .NET** obciążeń i następnie **Modyfikuj** przycisku.
   >
   > ![Otwórz łącze w Instalatorze programu Visual Studio](media/tutorial-projects-open-installer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. W obszarze **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy lub menu kontekstowe **rozwiązania "QuickSolution"** , wybierz **Dodaj** > **Nowy projekt**.

   Zostanie otwarte okno dialogowe z komunikatem **Dodawanie nowego projektu**.

1. Wprowadź **pusty** tekst w polu wyszukiwania u góry, a następnie wybierz **Visual Basic** w obszarze **Język**.

1. Wybierz szablon **pustego projektu (.NET Framework)** , a następnie wybierz przycisk **dalej**.

1. Nazwij projekt **QuickDate**, a następnie wybierz pozycję **Utwórz**.

   Projekt o nazwie QuickDate wyświetlany pod rozwiązania w **Eksploratora rozwiązań**. Obecnie zawiera jednego pliku o nazwie *App.config*.

   > [!NOTE]
   > Jeśli nie widzisz szablonu **pustego projektu (.NET Framework)** , musisz zainstalować **środowisko deweloperskie programu .NET Desktop** *.* Visual Studio używa Instalacja oparta na obciążenie można instalować tylko składniki potrzebne do typ pracy deweloperskiej, co możesz zrobić. Prostym sposobem na zainstalowanie nowego obciążenia podczas tworzenia nowego projektu jest wybranie linku **Zainstaluj więcej narzędzi i funkcji** pod tekstem, który **nie jest szukany?** . Po uruchomieniu Instalatora programu Visual Studio wybierz **programowanie aplikacji klasycznych dla platformy .NET** obciążeń i następnie **Modyfikuj** przycisku.
   >
   > ![Link Instalatora w programie Visual Studio 2019](../media/vs-2019/tutorial-projects-open-installer.png)

::: moniker-end

## <a name="add-an-item-to-the-project"></a>Dodaj element do projektu

Mamy pusty projekt. Dodajmy pliku kodu.

1. Z menu kliknij prawym przyciskiem myszy lub kontekst **QuickDate** projektu w **Eksploratora rozwiązań**, wybierz **Dodaj** > **nowy element** .

   **Dodaj nowy element** zostanie otwarte okno dialogowe.

1. Rozwiń węzeł **wspólne elementy**, a następnie wybierz pozycję **kod**. W środkowym okienku wybierz **klasy** szablon elementu. Nazwa klasy **kalendarza**, a następnie wybierz **Dodaj** przycisku.

   Plik o nazwie *Calendar. vb* został dodany do projektu. *. Vb* na końcu to rozszerzenie pliku, które ma Visual Basic plików kodu. Plik jest wyświetlany w hierarchii projektu wizualizacji w **Eksplorator rozwiązań**i jego zawartość jest otwarta w edytorze.

1. Zastąp zawartość pliku *Calendar. vb* następującym kodem:

   ```vb
   Class Calendar
       Public Shared Function GetCurrentDate() As Date
           Return DateTime.Now.Date
       End Function
   End Class
   ```

   Klasa `Calendar` zawiera pojedynczą funkcję, `GetCurrentDate`, która zwraca bieżącą datę.

1. Otwórz właściwości projektu, klikając dwukrotnie **mój projekt** w **Eksplorator rozwiązań**. Na karcie **aplikacja** Zmień **Typ aplikacji** na **Biblioteka klas**. Ten krok jest niezbędny do pomyślnego skompilowania projektu.

1. Skompiluj projekt, klikając prawym przyciskiem myszy pozycję **QuickDate** w **Eksplorator rozwiązań** i wybierając pozycję **Kompiluj**. W oknie **danych wyjściowych** powinien zostać wyświetlony komunikat pomyślne skompilowanie.

## <a name="add-a-second-project"></a>Dodasz drugi projekt

Rozwiązanie to często dotyczy rozwiązań zawierających więcej niż jeden projekt i często te projekty odwołują się do siebie. Niektóre projekty w rozwiązaniu może być bibliotek klas, niektóre pliku wykonywalnego aplikacji i może spowodować projektów testów jednostkowych lub witryn sieci Web.

Dodajmy projektu testu jednostkowego do naszego rozwiązania. Teraz Zaczniemy z szablonu projektu, nie mamy dodać plik dodatkowego kodu do projektu.

1. Z menu kliknij prawym przyciskiem myszy lub kontekst **rozwiązania "QuickSolution"** w **Eksploratora rozwiązań**, wybierz **Dodaj** > **nowy projekt**.

::: moniker range="Vs-2017"

2. W okienku po lewej stronie rozwiń **języka Visual Basic** i wybierz polecenie **testu** kategorii. W środkowym okienku wybierz **projekt testów jednostkowych (.NET Framework)** szablonu projektu. Nazwij projekt **Quicktest**, a następnie wybierz przycisk **OK**.

   Drugi projekt jest dodawany do **Eksploratora rozwiązań**, a plik o nazwie *UnitTest1.vb* zostanie otwarty w edytorze.

   ![Eksploratorze rozwiązań Visual Studio za pomocą dwóch projektów](media/tutorial-projects-solution-explorer-vb.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. W oknie dialogowym **Dodawanie nowego projektu** wprowadź **test jednostkowy** tekstu w polu wyszukiwania u góry, a następnie wybierz **Visual Basic** w obszarze **Język**.

3. Wybierz szablon projektu **test jednostkowy (.NET Framework)** , a następnie wybierz przycisk **dalej**.

4. Nazwij projekt **Quicktest**, a następnie wybierz pozycję **Utwórz**.

   Drugi projekt jest dodawany do **Eksploratora rozwiązań**, a plik o nazwie *UnitTest1.vb* zostanie otwarty w edytorze.

::: moniker-end

## <a name="add-a-project-reference"></a>Dodaj odwołanie do projektu

Będziemy używać nowego projektu testu jednostkowego do testowania naszych method in Class metoda **QuickDate** projektu, dlatego musimy dodać odwołanie do tego projektu. Spowoduje to utworzenie *zależności kompilacji* między dwa projekty, co oznacza, że podczas kompilowania rozwiązania **QuickDate** powstała przed **QuickTest**.

1. Wybierz **odwołania** w węźle **QuickTest** projektu i wybierz z menu kliknij prawym przyciskiem myszy lub kontekst **Dodaj odwołanie**.

   ![Dodaj odwołanie do menu](media/tutorial-projects-add-reference-vb.png)

   **Menadżer odwołań** zostanie otwarte okno dialogowe.

1. W okienku po lewej stronie rozwiń **projektów** i wybierz polecenie **rozwiązania**. W środkowym okienku wybierz pole wyboru obok **QuickDate**, a następnie wybierz **OK** przycisku.

   Odwołanie do **QuickDate** projekt jest dodawany.

## <a name="add-test-code"></a>Dodaj kod testowy

1. Teraz dodamy kod testu do pliku z kodem języka Visual Basic. Zastąp zawartość *UnitTest1.vb* następującym kodem.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(Date.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   Zobaczysz czerwoną część kodu. Naprawimy ten błąd, wprowadzając projekt testowy [przyjaznego zestawu](/dotnet/visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies) do **QuickDate** projektu.

1. W projekcie **QuickDate** Otwórz plik *Calendar. vb* , jeśli nie jest jeszcze otwarty, i Dodaj następującą [instrukcję Imports](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) i atrybut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>, aby rozwiązać błąd w projekcie testowym.

   ```vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("QuickTest")>
   ```

   Plik kodu powinna wyglądać następująco:

   ![Kod Visual Basic](media/tutorial-projects-code-vb.png)

## <a name="project-properties"></a>Właściwości projektu

Wiersz w pliku *Calendar. vb* , który zawiera atrybut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>, odwołuje się do nazwy zestawu (nazwy pliku) projektu **Quicktest** . Nazwa zestawu może nie być taka sama jak nazwa projektu. Aby znaleźć nazwy zestawu projektu, otwórz właściwości projektu.

1. W **Eksploratora rozwiązań**, wybierz opcję **QuickTest** projektu. Wybierz z menu kliknij prawym przyciskiem myszy lub kontekst **właściwości**, lub po prostu naciśnij **Alt**+**Enter**. (Możesz również kliknąć dwukrotnie pozycję **mój projekt** w **Eksplorator rozwiązań**).

   *Strony właściwości* projektu otwartego na karcie **aplikacja** . Strony właściwości zawierają różne ustawienia dla projektu. Należy zauważyć, że nazwa zestawu **QuickTest** projekt jest w rzeczywistości "QuickTest". Jeśli chcesz je zmienić, oznacza to, gdzie sposób, jak. Następnie podczas tworzenia projektu testowego, wynikowy plik binarny może zmiany nazwy z *QuickTest.dll* możesz wybrać.

   ![Właściwości projektu](../media/tutorial-projects-properties.png)

1. Zapoznaj się z innych kartach stron właściwości projektu, taki jak **skompilować** i **ustawienia**. Te karty są różne dla różnych typów projektów.

## <a name="optional-run-the-test"></a>Obowiązkowe Uruchom test

Jeśli chcesz sprawdzić, czy działa testu jednostkowego, wybierz opcję **Test** > **Uruchom** > **wszystkie testy** z paska menu. Wywołuje okno **Eksploratora testów** zostanie otwarta, a powinna być wyświetlana **TestGetCurrentDate** przebiegów testów.

![Eksplorator tekstów w programie Visual Studio pokazujący zakończony test](../media/tutorial-projects-test-explorer.png)

> [!TIP]
> Jeśli **Eksplorator testów** nie automatycznie, otwórz go, wybierając **testu** > **Windows** > **Eksplorator testów** z paska menu.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej na temat programu Visual Studio, należy rozważyć utworzenie aplikacji, postępując zgodnie z jednym z [samouczków Visual Basic](index.yml).

## <a name="see-also"></a>Zobacz także

- [Tworzenie projektów i rozwiązań](../../ide/creating-solutions-and-projects.md)
- [Zarządzanie właściwościami projektów i rozwiązań](../../ide/managing-project-and-solution-properties.md)
- [Zarządzanie odwołaniami w projekcie](../../ide/managing-references-in-a-project.md)
- [Tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE — omówienie](../../get-started/visual-studio-ide.md)
