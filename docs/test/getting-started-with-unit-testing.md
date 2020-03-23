---
title: Wprowadzenie do testowania jednostkowego
ms.date: 03/04/2020
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90c3cbdee722c4cf12c515f06659cc03f3179e1e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "78289857"
---
# <a name="get-started-with-unit-testing"></a>Wprowadzenie do testowania jednostkowego

Za pomocą programu Visual Studio do definiowania i uruchamiania testów jednostkowych w celu utrzymania kondycji kodu, zapewnienia pokrycia kodu i znajdowania błędów i błędów, zanim klienci to zrobią. Często uruchamiaj testy jednostkowe, aby upewnić się, że kod działa poprawnie.

## <a name="create-unit-tests"></a>Tworzenie testów jednostkowych

W tej sekcji opisano sposób tworzenia projektu testu jednostkowego.

1. Otwórz projekt, który chcesz przetestować w programie Visual Studio.

   Na potrzeby demonstrowania przykładowego testu jednostkowego w tym artykule testuje prosty projekt "Hello World" o nazwie **HelloWorldCore**. Przykładowy kod dla takiego projektu jest następujący:

   ```csharp
   namespace HelloWorldCore

      public class Program
      {
         public static void Main()
         {
            Console.WriteLine("Hello World!");
         }
      }
   ```

1. W **Eksploratorze rozwiązań**wybierz węzeł rozwiązania. Następnie z górnego paska menu wybierz pozycję **Plik** > **Dodaj** > **nowy projekt**.

1. W oknie dialogowym nowego projektu znajdź szablon projektu testu jednostkowego dla struktury testowej, której chcesz użyć, i wybierz go.

   ::: moniker range=">=vs-2019"

   ![Szablon projektu testu jednostkowego w programie Visual Studio 2019](media/vs-2019/add-new-test-project.png)

   Kliknij **przycisk Dalej**, wybierz nazwę projektu testowego, a następnie kliknij przycisk **Utwórz**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Szablon projektu testu jednostkowego w programie Visual Studio 2019](media/mstest-test-project-template.png)

   Wybierz nazwę projektu testowego, a następnie kliknij przycisk **OK**.

   ::: moniker-end

   Projekt zostanie dodany do rozwiązania.

   ![Projekt testu jednostkowego w Eksploratorze rozwiązań](media/vs-2019/solution-explorer.png)

1. W projekcie testu jednostkowego dodaj odwołanie do projektu, który chcesz przetestować, klikając prawym przyciskiem myszy **pozycję Odwołania** lub **zależności,** a następnie wybierając pozycję **Dodaj odwołanie**.

1. Wybierz projekt zawierający kod, który będzie testowany, i kliknij przycisk **OK**.

   ![Dodawanie odwołania do projektu w programie Visual Studio](media/vs-2019/reference-manager.png)

1. Dodaj kod do metody badania jednostkowego.

   Na przykład dla projektu MSTest można użyć następującego kodu.

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      [TestClass]
      public class UnitTest1
      {
         private const string Expected = "Hello World!";
         [TestMethod]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

   Lub dla projektu NUnit, można użyć następującego kodu.

   ```csharp
   using using NUnit.Framework;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
      [TestClass]
      public class Tests
      {
         private const string Expected = "Hello World!";

         [SetUp]
         public void Setup()
         {
         }
         [Test]
         public void TestMethod1()
         {
            using (var sw = new StringWriter())
            {
               Console.SetOut(sw);
               HelloWorldCore.Program.Main();

               var result = sw.ToString().Trim();
               Assert.AreEqual(Expected, result);
            }
         }
      }
   }
   ```

> [!TIP]
> Aby uzyskać więcej informacji na temat tworzenia testów jednostkowych, zobacz [Tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego](walkthrough-creating-and-running-unit-tests-for-managed-code.md).

## <a name="run-unit-tests"></a>Uruchamianie testów jednostkowych

1. Otwórz [Eksploratora testów](../test/run-unit-tests-with-test-explorer.md).

   ::: moniker range=">=vs-2019"
   Aby otworzyć Eksploratora testów, **wybierz** > **eksploratora testów** z górnego paska menu.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Aby otworzyć Eksploratora testów, wybierz pozycję > **Testuj** > **Eksploratora windowsów** na górnym pasku menu. **Test**
   ::: moniker-end

1. Uruchom testy jednostkowe, klikając przycisk **Uruchom wszystko**.

   ![Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](media/vs-2019/test-explorer-run-all.png)

   Po zakończeniu testów zielony znacznik wyboru wskazuje, że test został zakończony. Czerwona ikona "x" wskazuje, że test nie powiódł się.

   ![Przeglądanie wyników testów jednostkowych w Eksploratorze testów](media/vs-2019/unit-test-passed.png)

> [!TIP]
> [Eksploratora testów](../test/run-unit-tests-with-test-explorer.md) służy do uruchamiania testów jednostkowych z wbudowanej struktury testów (MSTest) lub z platform testowych innych firm. Testy można grupować w kategorie, filtrować listę testów oraz tworzyć, zapisywać i uruchamiać listy odtwarzania testów. Można również debugować testy i analizować wydajność testu i pokrycie kodu.

## <a name="view-live-unit-test-results"></a>Zobacz wyniki testu jednostkowego na żywo

Jeśli używasz mstest, xUnit lub NUnit testowania struktury w programie Visual Studio 2017 lub nowszych, można zobaczyć wyniki na żywo testów jednostkowych.

> [!NOTE]
> Testy jednostkowe na żywo są dostępne tylko w wersji Enterprise.

1. Włącz testowanie jednostek na żywo z menu **Test,** wybierając **opcję Start** > **testowania jednostek** > na żywo **.**

   ::: moniker range="vs-2017"

   ![Włączanie testowania jednostek na żywo](media/live-test-results-start.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Rozpoczynanie testowania jednostkowego na żywo w programie Visual Studio 2019](media/vs-2019/start-live-unit-testing.png)

   ::: moniker-end

1. Wyświetlanie wyników testów w oknie edytora kodu podczas pisania i edytowania kodu.

   ![Zobacz wyniki testów](media/vs-2019/live-unit-testing-results.png)

1. Kliknij wskaźnik wyników testu, aby wyświetlić więcej informacji, takich jak nazwy testów, które obejmują tę metodę.

   ![Wybieranie wskaźników wyników testu](media/vs-2019/live-unit-testing-details.png)

Aby uzyskać więcej informacji na temat testowania jednostek na żywo, zobacz [Testowanie jednostek na żywo](../test/live-unit-testing-intro.md).

## <a name="generate-unit-tests-with-intellitest"></a>Generowanie testów jednostkowych za pomocą funkcji IntelliTest

Po uruchomieniu IntelliTest, można zobaczyć, które testy są niepowodzeniem i dodać dowolny kod niezbędne, aby je naprawić. Można wybrać, które z wygenerowanych testów, aby zapisać w projekcie testowym, aby zapewnić pakiet regresji. Po zmianie kodu uruchom ponownie IntelliTest, aby zachować wygenerowane testy w synchronizacji ze zmianami kodu. Aby dowiedzieć się, jak to zrobić, zobacz [Generowanie testów jednostkowych dla kodu za pomocą intellitestu](../test/generate-unit-tests-for-your-code-with-intellitest.md).

> [!TIP]
> IntelliTest jest dostępny tylko dla kodu zarządzanego, który jest przeznaczony dla programu .NET Framework.

![Generowanie testów jednostkowych za pomocą intellitestu](media/intellitest.png)

## <a name="analyze-code-coverage"></a>Analizowanie pokrycia kodu

Aby określić, jaka część kodu projektu jest faktycznie testowana przez zakodowane testy, takie jak testy jednostkowe, można użyć funkcji pokrycia kodu programu Visual Studio. Aby skutecznie chronić przed błędami, testy powinny wykonywać dużą część kodu. Aby dowiedzieć się, jak to zrobić, zobacz [Używanie pokrycia kodu w celu określenia ilości testowanego kodu.](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)

## <a name="use-a-third-party-test-framework"></a>Korzystanie z struktury testów innych firm

Testy jednostkowe można uruchamiać w programie Visual Studio przy użyciu struktur testowych innych firm, takich jak Boost, Google i NUnit. Użyj **Menedżera pakietów NuGet,** aby zainstalować pakiet NuGet dla wybranej struktury. Lub dla NUnit i xUnit struktury testów Visual Studio zawiera wstępnie skonfigurowane szablony projektu testowego, które zawierają niezbędne pakiety NuGet.

Aby utworzyć testy jednostkowe, które używają [NUnit:](https://nunit.org/)

1. Otwórz rozwiązanie, które zawiera kod, który chcesz przetestować.

2. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratorze rozwiązań** i wybierz pozycję **Dodaj** > **nowy projekt**.

3. Wybierz szablon projektu **projektu testu NUnit.**

   ::: moniker range=">=vs-2019"

   ![Szablon projektu testu NUnit w programie Visual Studio 2019](media/vs-2019/nunit-test-project-template.png)

   Kliknij **przycisk Dalej**, nazwij projekt, a następnie kliknij przycisk **Utwórz**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   Nazwij projekt, a następnie kliknij przycisk **OK,** aby go utworzyć.

   ::: moniker-end

   Szablon projektu zawiera odwołania NuGet do NUnit i NUnit3TestAdapter.

   ![Zależności NUnit NuGet w Eksploratorze rozwiązań](media/vs-2019/nunit-nuget-dependencies.png)

4. Dodaj odwołanie z projektu testowego do projektu, który zawiera kod, który chcesz przetestować.

   Kliknij prawym przyciskiem myszy projekt w **Eksploratorze rozwiązań,** a następnie wybierz polecenie **Dodaj** > **odwołanie**. (Można również dodać odwołanie z menu prawym przyciskiem myszy węzła **Odwołania** lub **zależności).**

5. Dodaj kod do metody testowej.

   ![Dodawanie kodu do pliku kodu testu jednostkowego](media/vs-2019/unit-test-method.png)

6. Uruchom test z **Eksploratora testów** lub klikając prawym przyciskiem myszy kod testu i wybierając **polecenie Uruchom testy.**

## <a name="see-also"></a>Zobacz też

* [Przewodnik: tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
* [Polecenie Utwórz testy jednostkowe](create-unit-tests-menu.md)
* [Generowanie testów za pomocą intellitestu](generate-unit-tests-for-your-code-with-intellitest.md)
* [Uruchamianie testów za pomocą Eksploratora testów](run-unit-tests-with-test-explorer.md)
* [Analizowanie pokrycia kodu](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
