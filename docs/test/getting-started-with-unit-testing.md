---
title: Wprowadzenie do testów jednostkowych
ms.date: 02/13/2020
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ffbc5c6730fb4ca4d2f39732ad2a595de15bbf2
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77279331"
---
# <a name="get-started-with-unit-testing"></a>Wprowadzenie do testów jednostkowych

Za pomocą programu Visual Studio można definiować i uruchamiać testy jednostkowe, aby zachować kondycję kodu, zapewnić pokrycie kodu i znajdować błędy i usterki przed klientami. Regularnie uruchamiaj testy jednostkowe, aby upewnić się, że kod działa prawidłowo.

## <a name="create-unit-tests"></a>Utwórz testy jednostkowe

W tej sekcji opisano, jak utworzyć projekt testu jednostkowego.

1. Otwórz projekt, który chcesz przetestować w programie Visual Studio.

   W celach demonstrujących przykładowy test jednostkowy ten artykuł służy do testowania prostego projektu "Hello world" o nazwie **HelloWorldCore**. Przykładowy kod dla takiego projektu jest następujący:

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

1. W **Eksplorator rozwiązań**wybierz węzeł rozwiązania. Następnie z górnego paska menu wybierz pozycję **plik** > **Dodaj** > **Nowy projekt**.

1. W oknie dialogowym Nowy projekt Znajdź szablon projektu test jednostkowy dla struktury testowej, która ma zostać użyta, i wybierz ją.

   ::: moniker range=">=vs-2019"

   ![Szablon projektu testów jednostkowych w programie Visual Studio 2019](media/vs-2019/add-new-test-project.png)

   Kliknij przycisk **dalej**, wybierz nazwę projektu testowego, a następnie kliknij przycisk **Utwórz**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Szablon projektu testów jednostkowych w programie Visual Studio 2019](media/mstest-test-project-template.png)

   Wybierz nazwę projektu testowego, a następnie kliknij przycisk **OK**.

   ::: moniker-end

   Projekt zostanie dodany do rozwiązania.

   ![Projekt testów jednostkowych w Eksplorator rozwiązań](media/vs-2019/solution-explorer.png)

1. W projekcie testów jednostkowych Dodaj odwołanie do projektu, który chcesz przetestować, klikając prawym przyciskiem myszy pozycję **odwołania** lub **zależności** , a następnie wybierając pozycję **Dodaj odwołanie**.

1. Wybierz projekt zawierający kod, który zostanie przetestowany, i kliknij przycisk **OK**.

   ![Dodaj odwołanie do projektu w programie Visual Studio](media/vs-2019/reference-manager.png)

1. Dodaj kod do metody test jednostkowy.

   Na przykład w przypadku projektu testowego MSTest lub NUnit można użyć poniższego kodu.

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

> [!TIP]
> Aby zapoznać się z bardziej szczegółowym przewodnikiem tworzenia testów jednostkowych, zobacz [Tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego](walkthrough-creating-and-running-unit-tests-for-managed-code.md).

## <a name="run-unit-tests"></a>Uruchamianie testów jednostkowych

1. Otwórz [Eksploratora testów](../test/run-unit-tests-with-test-explorer.md).

   ::: moniker range=">=vs-2019"
   Aby otworzyć Eksploratora testów, wybierz polecenie **testuj** > **Eksploratorze testów** z górnego paska menu.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Aby otworzyć Eksploratora testów, wybierz polecenie **testuj** > **Windows** > **Eksplorator testów** z górnego paska menu.
   ::: moniker-end

1. Uruchom testy jednostkowe, klikając pozycję **Uruchom wszystkie**.

   ![Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](media/vs-2019/test-explorer-run-all.png)

   Po zakończeniu testów zielony znacznik wyboru wskazuje, że test zakończył się pomyślnie. Czerwona ikona "x" wskazuje, że test zakończył się niepowodzeniem.

   ![Przejrzyj wyniki testu jednostkowego w Eksploratorze testów](media/vs-2019/unit-test-passed.png)

> [!TIP]
> [Eksploratora testów](../test/run-unit-tests-with-test-explorer.md) można użyć do uruchomienia testów jednostkowych z wbudowanej struktury testowej (MSTest) lub innych firm. Można grupować testy do kategorii, filtrować listę testów oraz tworzyć, zapisywać i uruchamiać listy odtwarzania testów. Można również debugować testy i analizować wydajność testów i pokrycie kodu.

## <a name="view-live-unit-test-results"></a>Wyświetl wyniki testów jednostkowych na żywo

Jeśli używasz platformy testowania MSTest, xUnit lub NUnit w programie Visual Studio 2017 lub nowszym, możesz zobaczyć wyniki testów jednostkowych na żywo.

> [!NOTE]
> Testy jednostkowe na żywo są dostępne tylko w wersji Enterprise Edition.

1. Włącz funkcję Live Unit Testing z menu **test** , wybierając > **testowy** **Live Unit Testing** > **Start**.

   ::: moniker range="vs-2017"

   ![Włącz testy jednostkowe na żywo](media/live-test-results-start.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Uruchamianie testów jednostkowych na żywo w programie Visual Studio 2019](media/vs-2019/start-live-unit-testing.png)

   ::: moniker-end

1. Wyświetl wyniki testów w oknie edytora kodu podczas pisania i edycji kodu.

   ![Wyświetl wyniki testów](media/vs-2019/live-unit-testing-results.png)

1. Kliknij wskaźnik wyniku testu, aby wyświetlić więcej informacji, takich jak nazwy testów, które obejmują tę metodę.

   ![Wybierz wskaźniki wyniku testu](media/vs-2019/live-unit-testing-details.png)

Aby uzyskać więcej informacji na temat testów jednostkowych na żywo, zobacz [Live Unit Testing](../test/live-unit-testing-intro.md).

## <a name="generate-unit-tests-with-intellitest"></a>Generowanie testów jednostkowych za pomocą funkcji IntelliTest

Po uruchomieniu programu IntelliTest można zobaczyć, które testy kończą się niepowodzeniem i dodać kod, aby rozwiązać ten problem. Możesz wybrać, które wygenerowanych testów, aby zapisać do projektu testowego, aby zapewnić mechanizm regresji. W przypadku zmiany kodu, należy ponownie uruchomić program IntelliTest w celu synchronizowania wygenerowanych testów wprowadzania zmian w kodzie. Aby dowiedzieć się, jak to zrobić, zobacz [generowanie testów jednostkowych dla kodu za pomocą IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md).

> [!TIP]
> IntelliTest jest dostępny tylko dla kodu zarządzanego, który jest przeznaczony dla .NET Framework.

![Generowanie testów jednostkowych za pomocą IntelliTest](media/intellitest.png)

## <a name="analyze-code-coverage"></a>Analizowanie pokrycia kodu

Aby określić, jaka część kodu projektu jest faktycznie testowana przez zakodowane testy, takie jak testy jednostkowe, można użyć funkcji pokrycia kodu programu Visual Studio. Aby skutecznie zabezpieczyć się przed błędami, testy powinny korzystać z dużej proporcji kodu. Aby dowiedzieć się, jak [sprawdzić, ile kodu jest testowany, zobacz Użycie pokrycia kodu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="use-a-third-party-test-framework"></a>Korzystanie z platformy testów innych firm

Testy jednostkowe można uruchamiać w programie Visual Studio za pomocą platform testowych innych firm, takich jak zwiększanie, Google i NUnit. Użyj **Menedżera pakietów NuGet** , aby zainstalować pakiet NuGet dla wybranej platformy. W przypadku platform testowych NUnit i xUnit program Visual Studio zawiera wstępnie skonfigurowane szablony projektu testowego, które zawierają niezbędne pakiety NuGet.

Aby utworzyć testy jednostkowe używające [nunit](https://nunit.org/):

1. Otwórz rozwiązanie, które zawiera kod, który chcesz przetestować.

2. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj** > **Nowy projekt**.

3. Wybierz szablon projektu **testu nunit** .

   ::: moniker range=">=vs-2019"

   ![Szablon projektu testowego NUnit w programie Visual Studio 2019](media/vs-2019/nunit-test-project-template.png)

   Kliknij przycisk **dalej**, nazwij projekt, a następnie kliknij przycisk **Utwórz**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   Nazwij projekt, a następnie kliknij przycisk **OK** , aby go utworzyć.

   ::: moniker-end

   Szablon projektu zawiera odwołania NuGet do NUnit i NUnit3TestAdapter.

   ![NUnit zależności NuGet w Eksplorator rozwiązań](media/vs-2019/nunit-nuget-dependencies.png)

4. Dodaj odwołanie z projektu testowego do projektu, który zawiera kod, który chcesz przetestować.

   Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań**, a następnie wybierz pozycję **Dodaj** > **odwołanie**. (Można również dodać odwołanie z menu po kliknięciu prawym przyciskiem myszy węzła **odwołania** lub **zależności** ).

5. Dodaj kod do metody testowej.

   ![Dodaj kod do pliku kodu testu jednostkowego](media/vs-2019/unit-test-method.png)

6. Uruchom test z **Eksploratora testów** lub klikając prawym przyciskiem myszy kod testu i wybierając polecenie **Uruchom testy**.

## <a name="see-also"></a>Zobacz też

* [Przewodnik: Tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
* [Polecenie Utwórz testy jednostkowe](create-unit-tests-menu.md)
* [Generuj testy za pomocą IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [Uruchom testy za pomocą Eksploratora testów](run-unit-tests-with-test-explorer.md)
* [Analizowanie pokrycia kodu](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
