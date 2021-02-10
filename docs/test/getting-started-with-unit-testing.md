---
title: Rozpoczynanie pracy z testami jednostkowymi
description: Za pomocą programu Visual Studio można definiować i uruchamiać testy jednostkowe, aby zachować kondycję kodu, a następnie znajdować błędy i błędy przed klientami.
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
ms.openlocfilehash: c83b13b852b9ae53bd2218a62b6681478369df1b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970520"
---
# <a name="get-started-with-unit-testing"></a>Rozpoczynanie pracy z testami jednostkowymi

Za pomocą programu Visual Studio można definiować i uruchamiać testy jednostkowe, aby zachować kondycję kodu, zapewnić pokrycie kodu i znajdować błędy i usterki przed klientami. Regularnie uruchamiaj testy jednostkowe, aby upewnić się, że kod działa prawidłowo.

W tym artykule kod i ilustracje używają języka C#, ale koncepcje i funkcje dotyczą języków .NET, C++, Python, JavaScript i TypeScript.

## <a name="create-unit-tests"></a>Tworzenie testów jednostkowych

W tej sekcji opisano sposób tworzenia projektu testów jednostkowych.

1. Otwórz projekt, który chcesz przetestować w programie Visual Studio.

   Aby zapoznać się z przykładowym testem jednostkowym, ten artykuł służy do testowania prostego projektu C# "Hello world" o nazwie **HelloWorldCore**. Przykładowy kod dla takiego projektu jest następujący:

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

1. W **Eksplorator rozwiązań** wybierz węzeł rozwiązania. Następnie z górnego paska menu wybierz pozycję **plik**  >  **Dodaj**  >  **Nowy projekt**.

1. W oknie dialogowym Nowy projekt Znajdź szablon projektu test jednostkowy dla środowiska testowego, którego chcesz użyć, na przykład MSTest, i zaznacz go.

   Począwszy od programu Visual Studio 2017 w wersji 14,8, języki .NET zawierają wbudowane szablony dla NUnit i xUnit. W przypadku języka C++ należy wybrać platformę testową obsługiwaną przez język. W przypadku języka Python zapoznaj się z artykułem [Konfigurowanie testów jednostkowych w kodzie języka Python](../python/unit-testing-python-in-visual-studio.md) , aby skonfigurować projekt testowy.

   > [!TIP]
   > W przypadku języka C# można tworzyć projekty testów jednostkowych z kodu przy użyciu szybszej metody. Aby uzyskać więcej informacji, zobacz [Tworzenie projektów testów jednostkowych i metod testowych](../test/unit-test-basics.md#create-unit-test-projects-and-test-methods). Aby można było użyć tej metody z platformą .NET Core lub .NET Standard, wymagany jest program Visual Studio 2019.

   Na poniższej ilustracji przedstawiono test jednostkowy MSTest, który jest obsługiwany przez platformę .NET.

   ::: moniker range=">=vs-2019"

   ![Szablon projektu testów jednostkowych w programie Visual Studio 2019](media/vs-2019/add-new-test-project.png)

   Kliknij przycisk **dalej**, wybierz nazwę projektu testowego, a następnie kliknij przycisk **Utwórz**.

   ::: moniker-end

   ::: moniker range="vs-2017"

   ![Szablon projektu testów jednostkowych w programie Visual Studio 2019](media/mstest-test-project-template.png)

   Wybierz nazwę projektu testowego, na przykład HelloWorldTests, a następnie kliknij przycisk **OK**.

   ::: moniker-end

   Projekt zostanie dodany do rozwiązania.

   ![Projekt testów jednostkowych w Eksplorator rozwiązań](media/vs-2019/solution-explorer.png)

1. W projekcie testów jednostkowych Dodaj odwołanie do projektu, który chcesz przetestować, klikając prawym przyciskiem myszy pozycję **odwołania** lub **zależności** , a następnie wybierając pozycję **Dodaj odwołanie**.

1. Wybierz projekt zawierający kod, który zostanie przetestowany, i kliknij przycisk **OK**.

   ![Dodaj odwołanie do projektu w programie Visual Studio](media/vs-2019/reference-manager.png)

1. Dodaj kod do metody test jednostkowy.

   Na przykład można użyć poniższego kodu, wybierając poprawną kartę dokumentacji, która pasuje do struktury testowej: MSTest, NUnit lub xUnit (obsługiwana tylko w przypadku platformy .NET).

   # <a name="mstest"></a>[MSTest](#tab/mstest)

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

   # <a name="nunit"></a>[NUnit](#tab/nunit)

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

    # <a name="xunit"></a>[xUnit](#tab/xunit)

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

## <a name="run-unit-tests"></a>Uruchamianie testów jednostkowych

1. Otwórz [Eksploratora testów](../test/run-unit-tests-with-test-explorer.md).

   ::: moniker range=">=vs-2019"
   Aby otworzyć Eksploratora testów, wybierz **test** > **Eksplorator testów** z górnego paska menu (lub naciśnij **klawisze CTRL** + **E**, **T**).
   ::: moniker-end
   ::: moniker range="vs-2017"
   Aby otworzyć Eksploratora testów, wybierz pozycję **Testuj** >  > **Eksplorator testów** systemu Windows z górnego paska menu.
   ::: moniker-end

1. Uruchom testy jednostkowe, klikając pozycję **Uruchom wszystkie** (lub naciśnij **klawisze CTRL**  +  **R**, **V**).

   ![Przeprowadzanie testów jednostkowych za pomocą narzędzia Eksplorator testów](media/vs-2019/test-explorer-run-all.png)

   Po zakończeniu testów zielony znacznik wyboru wskazuje, że test zakończył się pomyślnie. Czerwona ikona "x" wskazuje, że test zakończył się niepowodzeniem.

   ![Przejrzyj wyniki testu jednostkowego w Eksploratorze testów](media/vs-2019/unit-test-passed.png)

> [!TIP]
> [Eksploratora testów](../test/run-unit-tests-with-test-explorer.md) można użyć do uruchomienia testów jednostkowych z wbudowanej struktury testowej (MSTest) lub innych firm. Można grupować testy do kategorii, filtrować listę testów oraz tworzyć, zapisywać i uruchamiać listy odtwarzania testów. Można również debugować testy i analizować wydajność testów i pokrycie kodu.

## <a name="view-live-unit-test-results-visual-studio-enterprise"></a>Wyświetl wyniki testów jednostkowych na żywo (Visual Studio Enterprise)

Jeśli używasz platformy testowania MSTest, xUnit lub NUnit w programie Visual Studio 2017 lub nowszym, możesz zobaczyć wyniki testów jednostkowych na żywo.

> [!NOTE]
> Aby wykonać te kroki, Visual Studio Enterprise jest wymagane.

1. Włącz funkcję Live Unit Testing z menu **test** , wybierając pozycję **test**  >  **Live Unit Testing**  >  **Rozpocznij**.

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

## <a name="use-a-third-party-test-framework"></a>Korzystanie z platformy testów innych firm

Testy jednostkowe można uruchamiać w programie Visual Studio za pomocą platform testowych innych firm, takich jak usprawnienia, Google i NUnit, w zależności od języka programowania. Aby korzystać z struktury innej firmy:

- Użyj **Menedżera pakietów NuGet** , aby zainstalować pakiet NuGet dla wybranej platformy.

- Architektury Począwszy od programu Visual Studio 2017 w wersji 14,6, program Visual Studio zawiera wstępnie skonfigurowane szablony projektów testowych dla platform testowych NUnit i xUnit. Szablony zawierają również niezbędne pakiety NuGet umożliwiające obsługę.

- Języków W programie Visual Studio 2017 i nowszych wersjach Niektóre platformy, takie jak zwiększanie wydajności, zostały już uwzględnione. Aby uzyskać więcej informacji, zobacz [pisać testy jednostkowe dla C/C++ w programie Visual Studio](../test/writing-unit-tests-for-c-cpp.md).

Aby dodać projekt testu jednostkowego:

1. Otwórz rozwiązanie, które zawiera kod, który chcesz przetestować.

2. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **Nowy projekt**.

3. Wybierz szablon projektu testu jednostkowego.

   W tym przykładzie wybierz pozycję [nunit](https://nunit.org/)

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

   Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Dodaj**  >  **odwołanie**. (Można również dodać odwołanie z menu po kliknięciu prawym przyciskiem myszy węzła **odwołania** lub **zależności** ).

5. Dodaj kod do metody testowej.

   ![Dodaj kod do pliku kodu testu jednostkowego](media/vs-2019/unit-test-method.png)

6. Uruchom test z **Eksploratora testów** lub klikając prawym przyciskiem myszy kod testu i wybierając polecenie **Uruchom testy** (lub **Ctrl**  +  **R**, **T**).

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Podstawowe informacje o teście jednostkowym](../test/unit-test-basics.md)

> [!div class="nextstepaction"]
> [Tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego](walkthrough-creating-and-running-unit-tests-for-managed-code.md)
