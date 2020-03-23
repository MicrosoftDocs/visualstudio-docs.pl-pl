---
title: Testy jednostkowe docelowe wcześniejszej wersji programu .NET Framework
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
author: mikejo5000
ms.openlocfilehash: 32380ddc802d1421f39d4920073fc277876cfef4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596024"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Jak: Konfigurowanie testów jednostkowych w celu kierowania na wcześniejszą wersję programu .NET Framework

Podczas tworzenia projektu testowego w programie Microsoft Visual Studio, najnowsza wersja programu .NET Framework jest domyślnie ustawiona jako obiekt docelowy. Ponadto w przypadku uaktualniania projektów testowych z poprzednich wersji programu Visual Studio są one uaktualniane do najnowszej wersji programu .NET Framework. Edytując właściwości projektu, można jawnie ponownie kierować projekt do wcześniejszych wersji programu .NET Framework.

Można utworzyć projekty testów jednostkowych, które są przeznaczone dla określonych wersji programu .NET Framework. Wersja docelowa musi mieć wersję 3.5 lub nowszą i nie może być wersją klienta. Program Visual Studio umożliwia następujące podstawowe wsparcie dla testów jednostkowych, które są przeznaczone dla określonych wersji:

- Można utworzyć projekty testów jednostkowych i kierować je do określonej wersji programu .NET Framework.

- Można uruchomić testy jednostkowe, które są przeznaczone dla określonej wersji programu .NET Framework z programu Visual Studio na komputerze lokalnym.

- Testy jednostkowe, które są przeznaczone dla określonej wersji programu .NET Framework przy użyciu *programu MSTest.exe* z wiersza polecenia.

- Można uruchomić testy jednostkowe na agenta kompilacji jako część kompilacji.

**Testowanie aplikacji programu SharePoint**

Możliwości wymienione powyżej umożliwiają również pisanie testów jednostkowych i testów integracji dla aplikacji programu SharePoint przy użyciu programu Visual Studio. Aby uzyskać więcej informacji na temat tworzenia aplikacji programu SharePoint za pomocą programu Visual Studio, zobacz [Tworzenie rozwiązań programu SharePoint](../sharepoint/create-sharepoint-solutions.md), [Tworzenie i debugowanie rozwiązań programu SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md) oraz [weryfikowanie i debugowanie kodu programu SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md).

**Ograniczenia**

Następujące ograniczenia mają zastosowanie podczas ponownego kierowania projektów testowych do korzystania z wcześniejszych wersji programu .NET Framework:

- W .NET Framework 3.5 multitargeting jest obsługiwany dla projektów testowych, które zawierają tylko testy jednostkowe. .NET Framework 3.5 nie obsługuje żadnego innego typu testu, takich jak kodowany interfejs użytkownika lub test obciążenia. Ponowne kierowanie jest blokowane dla typów testów innych niż testy jednostkowe.

- Wykonywanie testów, które są przeznaczone dla wcześniejszej wersji programu .NET Framework jest obsługiwany tylko w domyślnej karty hosta. Nie jest obsługiwany w ASP.NET karty hosta. ASP.NET aplikacje, które muszą być uruchamiane w kontekście serwera deweloperów ASP.NET, muszą być zgodne z bieżącą wersją programu .NET Framework.

- Obsługa zbierania danych jest wyłączona po uruchomieniu testów obsługujących multitargeting programu .NET Framework 3.5. Pokrycie kodu można uruchomić przy użyciu narzędzi wiersza polecenia programu Visual Studio.

- Testy jednostkowe korzystające z platformy .NET Framework 3.5 nie mogą być uruchamiane na komputerze zdalnym.

- Nie można kierować testów jednostkowych do wcześniejszych wersji klienta struktury.

## <a name="retargeting-for-visual-basic-unit-test-projects"></a>Retargeting dla projektów testowych jednostek języka Visual Basic

1. Utwórz nowy projekt **projektu testu jednostkowego** języka Visual Basic.

2. W **Eksploratorze rozwiązań**wybierz **polecenie Właściwości** z menu po kliknięciu prawym przyciskiem myszy nowego projektu testu języka Visual Basic.

     Zostaną wyświetlone właściwości projektu testu języka Visual Basic.

3. Na karcie **Kompilacja** wybierz pozycję **Zaawansowane opcje kompilacji,** jak pokazano na poniższej ilustracji.

     ![Zaawansowane opcje kompilacji](../test/media/howtoconfigureunittest35frameworka.png)

4. Użyj platformy **docelowej (wszystkie konfiguracje)** listy rozwijanej, aby zmienić platformę docelową na **.NET Framework 3.5** lub nowszą wersję, jak pokazano w objaśnieniu B na poniższej ilustracji. Nie należy określać wersji klienta.

     ![Lista&#45;upuszczania struktury docelowej w dół](../test/media/howtoconfigureunitest35frameworkstepb.png)

## <a name="retargeting-for-c-unit-test-projects"></a>Retargeting dla projektów testów jednostkowych języka C#

1. Utwórz nowy projekt **projektu testu jednostkowego** języka C#.

2. W **Eksploratorze rozwiązań**wybierz **polecenie Właściwości** z menu prawym przyciskiem myszy nowego projektu testowego języka C#.

   Właściwości projektu testowego języka C# są wyświetlane.

3. Na karcie **Aplikacja** wybierz pozycję **Framework docelowy**. Z listy rozwijanej wybierz **.NET Framework 3.5** lub nowszą wersję, jak pokazano na poniższej ilustracji. Nie należy określać wersji klienta.

   ![Lista&#45;upuszczania struktury docelowej w dół](../test/media/howtoconfigureunittest35frameworkcsharp.png)

## <a name="retargeting-for-ccli-unit-test-projects"></a>Retargeting dla projektów testowych jednostek C++/CLI

1. Utwórz nowy projekt **projektu testu jednostkowego** języka C++.

   > [!WARNING]
   > Aby utworzyć testy jednostkowe języka C++/CLI dla poprzedniej wersji platformy .NET dla programu Visual C++, należy użyć odpowiedniej wersji programu Visual Studio.

2. W **Eksploratorze rozwiązań**wybierz pozycję **Zwolnij projekt** z nowego projektu testowego języka C++.

3. W **Eksploratorze rozwiązań**wybierz niezaładowany projekt testowy języka C++, a następnie wybierz pozycję **Edytuj \<nazwę projektu>.vcxproj**.

   Plik *.vcxproj* zostanie otwarty w edytorze.

4. Ustaw `TargetFrameworkVersion` wersję 3.5 lub nowszą `PropertyGroup` w `"Globals"`wersji oznaczonej . Nie należy określać wersji klienta:

    ```xml
    <PropertyGroup Label="Globals">
        <TargetName>DefaultTest</TargetName>
        <ProjectTypes>{3AC096D0-A1C2-E12C-1390-A8335801FDAB};{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}</ProjectTypes>
        <ProjectGUID>{CE16D77A-E364-4ACD-948B-1EB6218B0EA3}</ProjectGUID>
        <TargetFrameworkVersion>3.5</TargetFrameworkVersion>
        <Keyword>ManagedCProj</Keyword>
        <RootNamespace>CPP_Test</RootNamespace>
      </PropertyGroup>
    ```

5. Zapisz i zamknij plik *.vcxproj.*

6. W **Eksploratorze rozwiązań**wybierz pozycję **Załaduj ponownie projekt** z menu po kliknięciu prawym przyciskiem myszy nowego projektu testowego języka C++.

## <a name="see-also"></a>Zobacz też

- [Tworzenie rozwiązań programu SharePoint](../sharepoint/create-sharepoint-solutions.md)
- [Tworzenie i debugowanie rozwiązań programu SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Okno dialogowe Ustawienia zaawansowanego kompilatora (Visual Basic)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)
