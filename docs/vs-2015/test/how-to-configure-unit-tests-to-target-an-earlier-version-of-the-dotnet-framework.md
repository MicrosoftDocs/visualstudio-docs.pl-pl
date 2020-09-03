---
title: 'Instrukcje: Konfigurowanie testów jednostkowych pod kątem wcześniejszej wersji .NET Framework | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: adb6c011-5abd-41d2-8ead-08cd7579bf37
caps.latest.revision: 14
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fd212eb304e6cba022b067b8b432cf00fc3f87ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660540"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Porady: konfigurowanie testów jednostkowych pod kątem starszej wersji oprogramowania .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas tworzenia projektu testowego w Microsoft Visual Studio, Najnowsza wersja .NET Framework jest domyślnie ustawiona jako element docelowy. Ponadto Jeśli uaktualniasz projekty testowe z poprzednich wersji programu Visual Studio, zostaną one uaktualnione pod kątem najnowszej wersji .NET Framework. Edytując właściwości projektu, można jawnie przekierować projekt do wcześniejszych wersji .NET Framework.

 Można tworzyć projekty testów jednostkowych, które są przeznaczone dla określonych wersji .NET Framework. Wersja doużywana musi mieć wartość 3,5 lub nowszą i nie może być wersją klienta. Program Visual Studio zapewnia podstawową pomoc techniczną dla testów jednostkowych przeznaczonych dla konkretnych wersji:

- Można tworzyć projekty testów jednostkowych i kierować je do określonej wersji .NET Framework.

- Można uruchomić testy jednostkowe przeznaczone dla określonej wersji .NET Framework z programu Visual Studio na komputerze lokalnym.

- Można uruchomić testy jednostkowe przeznaczone dla określonej wersji .NET Framework przy użyciu MSTest.exe z wiersza polecenia.

- Testy jednostkowe można uruchomić w agencie kompilacji w ramach kompilacji.

  **Testowanie aplikacji programu SharePoint**

  Wymienione powyżej możliwości pozwalają również pisać testy jednostkowe i testy integracji dla aplikacji programu SharePoint przy użyciu programu Visual Studio. [!INCLUDE[crabout](../includes/crabout-md.md)] jak opracowywać aplikacje programu SharePoint przy użyciu programu Visual Studio, zobacz [Tworzenie rozwiązań SharePoint](https://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631), [Kompilowanie i debugowanie rozwiązań SharePoint](https://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae) oraz [weryfikowanie i debugowanie kodu programu SharePoint](https://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c).

  **Ograniczenia**

  Następujące ograniczenia są stosowane po ponownym nakierowaniu projektów testowych do korzystania z wcześniejszych wersji .NET Framework:

- W .NET Framework 3,5, dla projektów testowych, które zawierają tylko testy jednostkowe, jest obsługiwana obsługa wieloelementowych. .NET Framework 3,5 nie obsługuje żadnego innego typu testowego, takiego jak kodowany interfejs użytkownika lub test obciążenia. Ponowne określanie wartości docelowej jest blokowane dla typów testów innych niż testy jednostkowe.

- Wykonywanie testów, które są przeznaczone dla starszej wersji .NET Framework jest obsługiwane tylko w domyślnym adapterze hosta. Nie jest obsługiwana na karcie hosta ASP.NET. Aplikacje ASP.NET, które muszą działać w kontekście serwera deweloperskiego ASP.NET, muszą być zgodne z bieżącą wersją .NET Framework.

- Obsługa zbierania danych jest wyłączona, gdy uruchamiasz testy, które obsługują wielodostępne .NET Framework 3,5. Pokrycie kodu można uruchomić przy użyciu narzędzi wiersza polecenia programu Visual Studio.

- Testy jednostkowe, które używają .NET Framework 3,5, nie mogą być uruchamiane na komputerze zdalnym.

- Nie można przekierować testów jednostkowych do wcześniejszych wersji klienta platformy.

### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-basic-unit-test-projects"></a>Ponowne kierowanie do określonej wersji .NET Framework dla projektów testów jednostkowych Visual Basic

1. Utwórz nowy projekt testu jednostkowego Visual Basic. W menu **plik** wybierz polecenie **Nowy** , a następnie wybierz **projekt**.

     Zostanie wyświetlone okno dialogowe **Nowy projekt** .

2. W obszarze **zainstalowane szablony**rozwiń węzeł **Visual Basic**. Wybierz pozycję **test** , a następnie wybierz szablon **projektu testowego** .

3. W polu tekstowym **Nazwa** wpisz nazwę projektu testowego Visual Basic a następnie wybierz **OK**.

4. W Eksplorator rozwiązań, wybierz **Właściwości** z menu skrótów nowego projektu testowego Visual Basic.

     Zostaną wyświetlone właściwości projektu testowego Visual Basic.

5. Na karcie **kompilacja** wybierz pozycję **Zaawansowane opcje kompilacji** , jak pokazano na poniższej ilustracji.

     ![Zaawansowane opcje kompilacji](../test/media/howtoconfigureunittest35frameworka.png "HowToConfigureUnitTest35FrameworkA")

6. Użyj listy rozwijanej **platformy docelowej (wszystkie konfiguracje)** , aby zmienić platformę docelową na **.NET Framework 3,5** lub nowszą, jak pokazano w objaśnieniu B na poniższej ilustracji. Nie należy określać wersji klienta.

     ![Docelowa lista rozwijana platformy docelowej&#45;](../test/media/howtoconfigureunitest35frameworkstepb.png "HowToConfigureUniTest35FrameworkStepB")

### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-c-unit-test-projects"></a>Ponowne kierowanie do określonej wersji .NET Framework dla projektów testów jednostkowych Visual C#

1. Utwórz nowy projekt testu jednostkowego w języku Visual C#. W menu **plik** wybierz polecenie **Nowy** , a następnie wybierz **projekt**.

     Zostanie wyświetlone okno dialogowe **Nowy projekt** .

2. W obszarze **zainstalowane szablony**rozwiń pozycję **Visual C#**. Wybierz pozycję **test** , a następnie wybierz szablon **projektu testowego** .

3. W polu tekstowym **Nazwa** wpisz nazwę projektu testowego Visual C#, a następnie wybierz **OK**.

4. W Eksplorator rozwiązań wybierz **Właściwości** z menu skrótów nowego projektu testowego języka Visual C#.

     Zostaną wyświetlone właściwości projektu testowego Visual C#.

5. Na karcie **aplikacja** wybierz **platformę docelową** , a następnie wybierz **.NET Framework 3,5** lub nowszą wersję z listy rozwijanej, aby zmienić element docelowy Framework.as pokazany na poniższej ilustracji. Nie należy określać wersji klienta.

     ![Docelowa lista rozwijana platformy docelowej&#45;](../test/media/howtoconfigureunittest35frameworkcsharp.png "HowToConfigureUnitTest35FrameworkCSharp")

### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-ccli-unit-test-projects"></a>Ponowne kierowanie do określonej wersji .NET Framework dla projektów testów jednostkowych C++/CLI

1. Utwórz nowy projekt jednostki testowej w języku C++. W menu **plik** wybierz pozycję **Nowy** , a następnie kliknij pozycję **projekt**.

     Zostanie wyświetlone okno dialogowe **Nowy projekt** .

    > [!WARNING]
    > Aby skompilować testy jednostkowe języka C++/CLI dla poprzedniej wersji programu .NET Framework dla Visual C++, należy użyć odpowiedniej wersji programu Visual Studio. Na przykład aby wskazać .NET Framework 3,5, należy zainstalować program [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] i [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] dodatek Service Pack 1.

2. W obszarze **zainstalowane szablony**rozwiń pozycję **Visual C + +**. Wybierz pozycję **test** , a następnie wybierz szablon **projektu testowego** .

3. W polu tekstowym **Nazwa** wpisz nazwę projektu testowego Visual C++ a następnie kliknij przycisk **OK**.

4. W Eksplorator rozwiązań wybierz pozycję **Zwolnij projekt** z nowego Visual C++ projektu testowego.

5. W Eksplorator rozwiązań wybierz niezaładowany Visual C++ projektu testowego, a następnie wybierz **Edytuj \<project name> . vcxproj**.

     Plik. vcxproj zostanie otwarty w edytorze.

6. Ustaw wartość w `TargetFrameworkVersion` wersji 3,5 lub nowszej w `PropertyGroup` etykiecie `"Globals"` . Nie należy określać wersji klienta:

    ```
    <PropertyGroup Label="Globals">
        <TargetName>DefaultTest</TargetName>
        <ProjectTypes>{3AC096D0-A1C2-E12C-1390-A8335801FDAB};{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}</ProjectTypes>
        <ProjectGUID>{CE16D77A-E364-4ACD-948B-1EB6218B0EA3}</ProjectGUID>
        <TargetFrameworkVersion>3.5</TargetFrameworkVersion>
        <Keyword>ManagedCProj</Keyword>
        <RootNamespace>CPP_Test</RootNamespace>
      </PropertyGroup>

    ```

7. Zapisz i zamknij plik. vcxproj.

8. W Eksplorator rozwiązań wybierz opcję Wybierz **Załaduj ponownie projekt** z menu skrótów nowego projektu testowego Visual C++.

## <a name="see-also"></a>Zobacz też
 [Tworzenie i uruchamianie testów jednostkowych dla istniejącego kodu](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173) [Tworzenie rozwiązań SharePoint](https://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631) tworzenie [i debugowanie](https://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae) [zaawansowanych ustawień kompilatora — okno dialogowe (Visual Basic)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)
