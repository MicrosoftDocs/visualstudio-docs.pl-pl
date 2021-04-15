---
title: Rozpoczynanie pracy z testami jednostkowymi
description: Użyj Visual Studio, aby zdefiniować i uruchomić testy jednostkowe w celu zachowania kondycji kodu oraz znalezienia błędów i błędów, zanim zrobią to klienci.
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: tutorial
helpviewer_keywords:
- unit testing, create unit test plans
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1e1576f8865fc5945514ce6965cdba66a1cfda55
ms.sourcegitcommit: 3985d0ae8d6332f4682c82a10897763173d52961
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2021
ms.locfileid: "107386053"
---
# <a name="get-started-with-unit-testing"></a>Rozpoczynanie pracy z testami jednostkowymi

Użyj Visual Studio, aby zdefiniować i uruchomić testy jednostkowe w celu zachowania kondycji kodu, zapewnienia pokrycia kodu oraz znalezienia błędów i błędów, zanim zrobią to klienci. Często uruchamiaj testy jednostkowe, aby upewnić się, że kod działa prawidłowo.

W tym artykule kod i ilustracje używają języka C#, ale pojęcia i funkcje dotyczą języków .NET, C++, Python, JavaScript i TypeScript.

## <a name="create-unit-tests"></a>Tworzenie testów jednostkowych

W tej sekcji opisano sposób tworzenia projektu testu jednostkowego.

1. Otwórz projekt, który chcesz przetestować w Visual Studio.

   Na potrzeby demonstrowania przykładowego testu jednostkowego ten artykuł testuje prosty projekt języka C# "Hello world" o nazwie **HelloWorldCore.** Przykładowy kod dla takiego projektu jest następujący:

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

1. W **Eksplorator rozwiązań** wybierz węzeł rozwiązania. Następnie na górnym pasku menu wybierz pozycję **Plik**  >  **Dodaj nowy**  >  **projekt.**

1. W oknie dialogowym nowy projekt znajdź szablon projektu testu jednostkowego dla struktury testów, której chcesz użyć, na przykład MSTest, i wybierz go.

   Począwszy od Visual Studio 2017 r. w wersji 14.8, języki .NET zawierają wbudowane szablony dla NUnit i xUnit. W przypadku języka C++ należy wybrać platformę testową obsługiwaną przez język. W przypadku języka Python zobacz [Konfigurowanie testowania jednostkowego w](../python/unit-testing-python-in-visual-studio.md) kodzie języka Python, aby skonfigurować projekt testowy.

   > [!TIP]
   > W przypadku języka C# można tworzyć projekty testów jednostkowych z kodu przy użyciu szybszej metody. Aby uzyskać więcej informacji, zobacz Create unit test projects and test methods (Tworzenie projektów [testów jednostkowych i metod testowych).](../test/unit-test-basics.md#create-unit-test-projects-and-test-methods) Aby użyć tej metody z programem .NET Core lub .NET Standard, Visual Studio 2019 jest wymagany.

   Na poniższej ilustracji przedstawiono test jednostkowy MSTest, który jest obsługiwany na .NET.

   ::: moniker range=">=vs-2019"

   ![Szablon projektu testu jednostkowego w Visual Studio 2019 r.](media/vs-2019/add-new-test-project.png)

   Kliknij **przycisk** Dalej, wybierz nazwę projektu testowego, a następnie kliknij pozycję **Utwórz**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Szablon projektu testu jednostkowego w Visual Studio 2019 r.](media/mstest-test-project-template.png)

   Wybierz nazwę projektu testowego, na przykład HelloWorldTests, a następnie kliknij przycisk **OK.**

   ::: moniker-end

   Projekt zostanie dodany do rozwiązania.

   ![Projekt testu jednostkowego w programie Eksplorator rozwiązań](media/vs-2019/solution-explorer.png)

1. W projekcie testu jednostkowego dodaj odwołanie do projektu, który chcesz  przetestować, klikając prawym przyciskiem myszy pozycję **Odwołania** lub zależności, a następnie wybierając polecenie **Dodaj odwołanie**.

1. Wybierz projekt zawierający testowy kod, a następnie kliknij przycisk **OK.**

   ![Dodawanie odwołania do projektu w Visual Studio](media/vs-2019/reference-manager.png)

1. Dodaj kod do metody testu jednostkowego.

   Na przykład możesz użyć następującego kodu, wybierając odpowiednią kartę dokumentacji, która pasuje do struktury testowej: MSTest, NUnit lub xUnit (obsługiwana tylko na platformie .NET).

   ### <a name="mstest"></a>[MSTest](#tab/mstest)

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

   ### <a name="nunit"></a>[NUnit](#tab/nunit)

   ```csharp
   using NUnit.Framework;
   using System.IO;
   using System;

   namespace HelloWorldTests
   {
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

    ### <a name="xunit"></a>[xUnit](#tab/xunit)

    ```csharp
    using System;
    using Xunit;
    using System.IO;
    
    namespace HelloWorldTests
    {
        public class UnitTest1
        {
            private const string Expected = "Hello World!";
            [Fact]
            public void Test1()
            {
                using (var sw = new StringWriter())
                {
                    Console.SetOut(sw);
                    HelloWorldCore.Program.Main();
    
                    var result = sw.ToString().Trim();
                    Assert.Equal(Expected, result);
                }
            }
        }
    }
    ```

    ---

## <a name="run-unit-tests"></a>Uruchamianie testów jednostkowych

1. Otwórz [Eksplorator testów.](../test/run-unit-tests-with-test-explorer.md)

   ::: moniker range=">=vs-2019"
   Aby otworzyć Eksploratora testów, wybierz **pozycję** > **Eksplorator testów** na górnym pasku menu (lub naciśnij klawisze **Ctrl** + **E,** **T**).
   ::: moniker-end
   ::: moniker range="vs-2017"
   Aby otworzyć Eksploratora testów, wybierz **pozycję Testuj** >  > **Eksploratora testów systemu** Windows na górnym pasku menu.
   ::: moniker-end

1. Uruchom testy jednostkowe, klikając pozycję **Uruchom wszystko** (lub naciśnij **klawisze Ctrl**  +  **R,** **V**).

   ![Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](media/vs-2019/test-explorer-run-all.png)

   Po zakończeniu testów zielony znacznik wyboru wskazuje, że test zakończył się pomyślnie. Czerwona ikona "x" wskazuje, że test zakończył się niepowodzeniem.

   ![Przeglądanie wyników testów jednostkowych w Eksploratorze testów](media/vs-2019/unit-test-passed.png)

> [!TIP]
> Eksplorator testów [umożliwia](../test/run-unit-tests-with-test-explorer.md) uruchamianie testów jednostkowych z wbudowanej struktury testów (MSTest) lub z platform testów innych firm. Testy można grupować w kategorie, filtrować listę testów oraz tworzyć, zapisywać i uruchamiać listy odtwarzania testów. Można również debugować testy i analizować wydajność testów oraz pokrycie kodu.

## <a name="view-live-unit-test-results-visual-studio-enterprise"></a>Wyświetlanie wyników testów jednostkowych na żywo (Visual Studio Enterprise)

Jeśli używasz struktury testowania MSTest, xUnit lub NUnit w programie Visual Studio 2017 lub nowszym, możesz zobaczyć wyniki testów jednostkowych na żywo.

> [!NOTE]
> Aby wykonać te kroki, Visual Studio Enterprise jest wymagana.

1. Włącz testy jednostkowe na żywo z menu **Test,** wybierając pozycję  >  **Test Live Unit Testing**  >  **Start.**

   ::: moniker range="vs-2017"

   ![Włączanie testów jednostkowych na żywo](media/live-test-results-start.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Rozpocznij testy jednostkowe na żywo w Visual Studio 2019 r.](media/vs-2019/start-live-unit-testing.png)

   ::: moniker-end

1. Wyświetlaj wyniki testów w oknie edytora kodu podczas pisania i edytowania kodu.

   ![Wyświetlanie wyników testów](media/vs-2019/live-unit-testing-results.png)

1. Kliknij wskaźnik wyniku testu, aby wyświetlić więcej informacji, takich jak nazwy testów, które obejmują tę metodę.

   ![Wybieranie wskaźników wyników testu](media/vs-2019/live-unit-testing-details.png)

Aby uzyskać więcej informacji na temat testów jednostkowych na żywo, zobacz [Live unit testing (Testy jednostkowe na żywo).](../test/live-unit-testing-intro.md)

## <a name="use-a-third-party-test-framework"></a>Używanie struktury testowej innej firmy

Testy jednostkowe można uruchamiać w Visual Studio przy użyciu platform testowych innych firm, takich jak Boost, Google i NUnit, w zależności od języka programowania. Aby użyć struktury innej firmy:

- Użyj **zestawu Menedżer pakietów NuGet,** aby zainstalować pakiet NuGet dla wybranej struktury.

- (.NET) Począwszy od Visual Studio 2017 r. w wersji 14.6, program Visual Studio zawiera wstępnie skonfigurowane szablony projektów testowych dla platform testowych NUnit i xUnit. Szablony zawierają również pakiety NuGet niezbędne do włączenia obsługi.

- (C++) W Visual Studio wersji 2017 i nowszych niektóre struktury, takie jak Boost, są już dołączone. Aby uzyskać więcej informacji, zobacz [Pisanie testów jednostkowych dla języka C/C++ w Visual Studio](../test/writing-unit-tests-for-c-cpp.md).

Aby dodać projekt testu jednostkowego:

1. Otwórz rozwiązanie zawierające kod, który chcesz przetestować.

2. Kliknij prawym przyciskiem myszy rozwiązanie na stronie **Eksplorator rozwiązań** a następnie wybierz **polecenie Dodaj** nowy  >  **projekt.**

3. Wybierz szablon projektu testu jednostkowego.

   W tym przykładzie wybierz pozycję [NUnit](https://nunit.org/)

   ::: moniker range=">=vs-2019"

   ![Szablon projektu testowego NUnit w Visual Studio 2019 r.](media/vs-2019/nunit-test-project-template.png)

   Kliknij **przycisk Dalej,** nadaj projektowi nazwę, a następnie kliknij pozycję **Utwórz**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   Nadaj projektowi nazwę, a następnie kliknij przycisk **OK,** aby go utworzyć.

   ::: moniker-end

   Szablon projektu zawiera odwołania NuGet do NUnit i NUnit3TestAdapter.

   ![Zależności nuGet NUnit w Eksplorator rozwiązań](media/vs-2019/nunit-nuget-dependencies.png)

4. Dodaj odwołanie z projektu testowego do projektu zawierającego kod, który chcesz przetestować.

   Kliknij prawym przyciskiem myszy projekt w **programie Eksplorator rozwiązań**, a następnie wybierz **pozycję Dodaj**  >  **odwołanie**. (Możesz również dodać odwołanie z menu dostępnego po kliknięciu prawym przyciskiem myszy węzła **Odwołania** **lub** Zależności).

5. Dodaj kod do metody testowej.

   ![Dodawanie kodu do pliku kodu testu jednostkowego](media/vs-2019/unit-test-method.png)

6. Uruchom test w **Eksploratorze testów** lub klikając prawym przyciskiem myszy kod testowy i wybierając polecenie Uruchom testy **(lub** **Ctrl**  +  **R,** **T**).

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Podstawowe informacje o teście jednostkowym](../test/unit-test-basics.md)

> [!div class="nextstepaction"]
> [Tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
