---
title: Samouczek projekty i rozwiązania Visual Basic
ms.date: 12/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: tutorial
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: c55f0bf2d36d06cc47e39086236b41d4cc8340c9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961614"
---
# <a name="learn-about-projects-and-solutions-using-visual-basic"></a>Więcej informacji na temat projektów i rozwiązań w języku Visual Basic

W tym artykule wprowadzające przedstawimy wyjaśniono tworzenie *rozwiązania* i *projektu* w programie Visual Studio. To rozwiązanie jest kontenerem, który służy do organizowania jeden lub więcej powiązanych projektów kodu, na przykład projekt biblioteki klas i odpowiedniego projektu testowego. Omówimy właściwości projektu i niektórych plików, który może zawierać. Również utworzymy odwołanie z jednego projektu do drugiego.

> [!TIP]
> Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

Firma Microsoft będzie konstruowania rozwiązania i projektu od podstaw w charakterze edukacyjnym ćwiczenia zrozumienie pojęcia projektu. Ogólne korzystający z programu Visual Studio, prawdopodobnie użyjesz niektóre z projektu różne *szablony* , program Visual Studio oferuje podczas tworzenia nowego projektu.

> [!NOTE]
> Rozwiązania i projekty nie są wymagane do tworzenia aplikacji w programie Visual Studio. Możesz też po prostu otwórz folder, który zawiera kod i uruchamiania kodowania, kompilowania i debugowania. Na przykład, jeśli można sklonować [GitHub](https://github.com/) repozytorium, może nie zawierać projektów programu Visual Studio i rozwiązania. Aby uzyskać więcej informacji, zobacz [tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions-and-projects"></a>Rozwiązania i projekty

Pomimo swojej nazwy rozwiązania nie jest "" (odpowiedź). To rozwiązanie jest po prostu kontener używane przez program Visual Studio do organizowania, jeden lub więcej powiązanych projektów. Po otwarciu rozwiązania w programie Visual Studio automatycznie ładuje wszystkie projekty, które zawiera rozwiązania.

### <a name="create-a-solution"></a>Tworzenie rozwiązania

Rozpoczniemy naszych badań, tworząc puste rozwiązanie. Po uzyskaniu znasz programu Visual Studio, prawdopodobnie nie będzie zaczniesz tworzyć puste rozwiązania bardzo często. Podczas tworzenia nowego projektu programu Visual Studio automatycznie tworzy rozwiązanie do przechowywania projektu, jeśli nie ma rozwiązania już otwarte.

1. Otwórz program Visual Studio.

1. Na pasku menu, czyli wiersz menu, takich jak **pliku** i **Edytuj**, wybierz **pliku** > **New**  >   **Projekt**.

   **Nowy projekt** zostanie otwarte okno dialogowe.

1. W okienku po lewej stronie rozwiń **inne typy projektów**, następnie wybierz **Visual Studio Solutions**. W środkowym okienku wybierz **puste rozwiązanie** szablonu. Nazwa rozwiązania **QuickSolution**, następnie wybierz **OK** przycisku.

   ![Pusty szablon rozwiązania w programie Visual Studio](../media/tutorial-projects-new-solution.png)

   **Strona startowa** zostanie zamknięty i rozwiązania zostaną wyświetlone w **Eksploratora rozwiązań** po prawej stronie okna programu Visual Studio. Prawdopodobnie użyjesz **Eksploratora rozwiązań** często, aby przeglądać zawartość Twoich projektów.

### <a name="add-a-project"></a>Dodaj projekt

Teraz Dodajmy nasz pierwszy projekt do rozwiązania. Firma Microsoft będzie rozpoczynać pusty projekt i dodać elementy, które należy do projektu.

1. Z menu kliknij prawym przyciskiem myszy lub kontekst **rozwiązania "QuickSolution"** w **Eksploratora rozwiązań**, wybierz **Dodaj** > **nowy projekt**.

   **Dodaj nowy projekt** zostanie otwarte okno dialogowe.

1. W okienku po lewej stronie rozwiń **języka Visual Basic** i wybierz polecenie **pulpitu Windows**. Następnie w środkowym okienku wybierz **pusty projekt (.NET Framework)** szablonu. Nadaj projektowi nazwę **QuickDate**, następnie wybierz **OK** przycisku.

   Projekt o nazwie QuickDate wyświetlany pod rozwiązania w **Eksploratora rozwiązań**. Obecnie zawiera jednego pliku o nazwie *App.config*.

   > [!NOTE]
   > Jeśli nie widzisz **języka Visual Basic** w lewym okienku okna dialogowego, musisz zainstalować **programowanie aplikacji klasycznych dla platformy .NET** programu Visual Studio *obciążenia*. Visual Studio używa Instalacja oparta na obciążenie można instalować tylko składniki potrzebne do typ pracy deweloperskiej, co możesz zrobić. Prosty sposób, aby zainstalować nowe obciążenie jest wybranie **Otwórz Instalator programu Visual Studio** łącze w lewym dolnym rogu **Dodaj nowy projekt** okno dialogowe. Po uruchomieniu Instalatora programu Visual Studio wybierz **programowanie aplikacji klasycznych dla platformy .NET** obciążeń i następnie **Modyfikuj** przycisku.

   ![Otwórz łącze w Instalatorze programu Visual Studio](media/tutorial-projects-open-installer-vb.png)

## <a name="add-an-item-to-the-project"></a>Dodaj element do projektu

Mamy pusty projekt. Dodajmy pliku kodu.

1. Z menu kliknij prawym przyciskiem myszy lub kontekst **QuickDate** projektu w **Eksploratora rozwiązań**, wybierz **Dodaj** > **nowy element** .

   **Dodaj nowy element** zostanie otwarte okno dialogowe.

1. Rozwiń **wspólne elementy**, następnie wybierz **kodu**. W środkowym okienku wybierz **klasy** szablon elementu. Nazwa klasy **kalendarza**, a następnie wybierz **Dodaj** przycisku.

   Plik o nazwie *Calendar.vb* zostanie dodany do projektu. *.Vb* na końcu jest rozszerzenie pliku, który znajduje się w plikach kodu języka Visual Basic. Plik pojawi się w hierarchii projektu wizualizacji w **Eksploratora rozwiązań**, a jego zawartość, Otwórz w edytorze.

1. Zastąp zawartość *Calendar.vb* pliku następującym kodem:

   ```vb
   Class Calendar
       Public Shared Function GetCurrentDate() As Date
           Return DateTime.Now.Date
       End Function
   End Class
   ```

   `Calendar` Klasa zawiera pojedynczą funkcję `GetCurrentDate`, która zwraca bieżącą datę.

1. Otwórz właściwości projektu, klikając dwukrotnie **mój projekt** w **Eksploratora rozwiązań**. Na **aplikacji** kartę, zmień **typ aplikacji** do **biblioteki klas**. Ten krok jest niezbędny pomyślnie skompilować projekt.

1. Skompiluj projekt, klikając prawym przyciskiem myszy **QuickDate** w **Eksploratora rozwiązań** i wybierając pozycję **kompilacji**. Powinien zostać wyświetlony komunikat pomyślne kompilacji w **dane wyjściowe** okna.

## <a name="add-a-second-project"></a>Dodasz drugi projekt

Jest typowe dla rozwiązań zawierała więcej niż jeden projekt, a często te projekty odwoływać się do siebie nawzajem. Niektóre projekty w rozwiązaniu może być bibliotek klas, niektóre pliku wykonywalnego aplikacji i może spowodować projektów testów jednostkowych lub witryn sieci Web.

Dodajmy projektu testu jednostkowego do naszego rozwiązania. Teraz Zaczniemy z szablonu projektu, nie mamy dodać plik dodatkowego kodu do projektu.

1. Z menu kliknij prawym przyciskiem myszy lub kontekst **rozwiązania "QuickSolution"** w **Eksploratora rozwiązań**, wybierz **Dodaj** > **nowy projekt**.

   **Dodaj nowy projekt** zostanie otwarte okno dialogowe.

1. W okienku po lewej stronie rozwiń **języka Visual Basic** i wybierz polecenie **testu** kategorii. W środkowym okienku wybierz **projekt testów jednostkowych (.NET Framework)** szablonu projektu. Nadaj projektowi nazwę **QuickTest**, a następnie wybierz **OK** przycisku.

   Drugi projekt jest dodawany do **Eksploratora rozwiązań**, a plik o nazwie *UnitTest1.vb* zostanie otwarty w edytorze.

   ![Eksploratorze rozwiązań Visual Studio za pomocą dwóch projektów](media/tutorial-projects-solution-explorer-vb.png)

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

   Zobaczysz czerwony symbol "falista" w obszarze część kodu. Naprawimy ten błąd, wprowadzając projekt testowy [przyjaznego zestawu](/dotnet/visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies) do **QuickDate** projektu.

1. Ponownie **QuickDate** otwarty projekt *Calendar.vb* plik, jeśli nie jest jeszcze otwarty, a następnie dodaj następujący kod [Imports — instrukcja](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) i <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu do Napraw błąd w projekcie testowym.

   ```vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("QuickTest")>
   ```

   Plik kodu powinna wyglądać następująco:

   ![Kod Visual Basic](media/tutorial-projects-code-vb.png)

## <a name="project-properties"></a>Właściwości projektu

Wiersz w *Calendar.vb* pliku, który zawiera <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut odwołuje się nazwa zestawu (nazwa pliku) **QuickTest** projektu. Nazwa zestawu może nie być taka sama jak nazwa projektu. Aby znaleźć nazwy zestawu projektu, otwórz właściwości projektu.

1. W **Eksploratora rozwiązań**, wybierz opcję **QuickTest** projektu. Wybierz z menu kliknij prawym przyciskiem myszy lub kontekst **właściwości**, lub po prostu naciśnij **Alt**+**Enter**. (Możesz również kliknąć dwukrotnie **mój projekt** w **Eksploratora rozwiązań**.)

   *Stron właściwości* dla projektu, Otwórz na **aplikacji** kartę. Strony właściwości zawierają różne ustawienia dla projektu. Należy zauważyć, że nazwa zestawu **QuickTest** projekt jest w rzeczywistości "QuickTest". Jeśli chcesz je zmienić, oznacza to, gdzie sposób, jak. Następnie podczas tworzenia projektu testowego, wynikowy plik binarny może zmiany nazwy z *QuickTest.dll* możesz wybrać.

   ![Właściwości projektu](../media/tutorial-projects-properties.png)

1. Zapoznaj się z innych kartach stron właściwości projektu, taki jak **skompilować** i **ustawienia**. Te karty są różne dla różnych typów projektów.

## <a name="optional-run-the-test"></a>(Opcjonalnie) Uruchom test

Jeśli chcesz sprawdzić, czy działa testu jednostkowego, wybierz opcję **Test** > **Uruchom** > **wszystkie testy** z paska menu. Wywołuje okno **Eksploratora testów** zostanie otwarta, a powinna być wyświetlana **TestGetCurrentDate** przebiegów testów.

![Test Explorer tekstu w programie Visual Studio przedstawiający przekazany](../media/tutorial-projects-test-explorer.png)

> [!TIP]
> Jeśli **Eksplorator testów** nie automatycznie, otwórz go, wybierając **testu** > **Windows** > **Eksplorator testów** z paska menu.

## <a name="next-steps"></a>Następne kroki

Jeśli chcesz dokładniej zbadać programu Visual Studio, należy rozważyć utworzenie aplikacji, wykonując jedną z [samouczki języka Visual Basic](index.yml).

## <a name="see-also"></a>Zobacz także

- [Tworzenie projektów i rozwiązań](../../ide/creating-solutions-and-projects.md)
- [Zarządzanie właściwościami projektów i rozwiązań](../../ide/managing-project-and-solution-properties.md)
- [Zarządzanie odwołaniami w projekcie](../../ide/managing-references-in-a-project.md)
- [Tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Visual Studio IDE — omówienie](../../get-started/visual-studio-ide.md)