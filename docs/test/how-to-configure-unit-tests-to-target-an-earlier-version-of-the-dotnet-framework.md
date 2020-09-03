---
title: Testy jednostkowe docelowe w starszej wersji .NET Framework
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
author: mikejo5000
ms.openlocfilehash: 670ec672c55d591496e26435db5a3112c345a44d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288172"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Instrukcje: Konfigurowanie testów jednostkowych pod kątem wcześniejszej wersji .NET Framework

Podczas tworzenia projektu testowego w Microsoft Visual Studio, Najnowsza wersja .NET Framework jest domyślnie ustawiona jako element docelowy. Ponadto Jeśli uaktualniasz projekty testowe z poprzednich wersji programu Visual Studio, zostaną one uaktualnione pod kątem najnowszej wersji .NET Framework. Edytując właściwości projektu, można jawnie przekierować projekt do wcześniejszych wersji .NET Framework.

Można tworzyć projekty testów jednostkowych, które są przeznaczone dla określonych wersji .NET Framework. Wersja doużywana musi mieć wartość 3,5 lub nowszą i nie może być wersją klienta. Program Visual Studio zapewnia podstawową pomoc techniczną dla testów jednostkowych przeznaczonych dla konkretnych wersji:

- Można tworzyć projekty testów jednostkowych i kierować je do określonej wersji .NET Framework.

- Można uruchomić testy jednostkowe przeznaczone dla określonej wersji .NET Framework z programu Visual Studio na komputerze lokalnym.

- Można uruchomić testy jednostkowe przeznaczone dla określonej wersji .NET Framework przy użyciu *MSTest.exe* z wiersza polecenia.

- Testy jednostkowe można uruchomić w agencie kompilacji w ramach kompilacji.

**Testowanie aplikacji programu SharePoint**

Wymienione powyżej możliwości pozwalają również pisać testy jednostkowe i testy integracji dla aplikacji programu SharePoint przy użyciu programu Visual Studio. Aby uzyskać więcej informacji o sposobach opracowywania aplikacji programu SharePoint przy użyciu programu Visual Studio, zobacz [Tworzenie rozwiązań SharePoint](../sharepoint/create-sharepoint-solutions.md), [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md) oraz [weryfikowanie i debugowanie kodu programu SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md).

**Ograniczenia**

Następujące ograniczenia są stosowane po ponownym nakierowaniu projektów testowych do korzystania z wcześniejszych wersji .NET Framework:

- W .NET Framework 3,5, dla projektów testowych, które zawierają tylko testy jednostkowe, jest obsługiwana obsługa wieloelementowych. .NET Framework 3,5 nie obsługuje żadnego innego typu testowego, takiego jak kodowany interfejs użytkownika lub test obciążenia. Ponowne określanie wartości docelowej jest blokowane dla typów testów innych niż testy jednostkowe.

- Wykonywanie testów, które są przeznaczone dla starszej wersji .NET Framework jest obsługiwane tylko w domyślnym adapterze hosta. Nie jest obsługiwana na karcie hosta ASP.NET. Aplikacje ASP.NET, które muszą działać w kontekście serwera deweloperskiego ASP.NET, muszą być zgodne z bieżącą wersją .NET Framework.

- Obsługa zbierania danych jest wyłączona, gdy uruchamiasz testy, które obsługują wielodostępne .NET Framework 3,5. Pokrycie kodu można uruchomić przy użyciu narzędzi wiersza polecenia programu Visual Studio.

- Testy jednostkowe, które używają .NET Framework 3,5, nie mogą być uruchamiane na komputerze zdalnym.

- Nie można przekierować testów jednostkowych do wcześniejszych wersji klienta platformy.

## <a name="retargeting-for-visual-basic-unit-test-projects"></a>Przekierowywanie dla projektów testów jednostkowych Visual Basic

1. Utwórz nowy projekt **projektu testu jednostkowego** Visual Basic.

2. W obszarze **Eksplorator rozwiązań**wybierz pozycję **Właściwości** w menu rozwijanym prawym przyciskiem myszy nowy Visual Basic projekt testowy.

     Zostaną wyświetlone właściwości projektu testowego Visual Basic.

3. Na karcie **Kompilowanie** wybierz pozycję **Zaawansowane opcje kompilacji** , jak pokazano na poniższej ilustracji.

     ![Zaawansowane opcje kompilacji](../test/media/howtoconfigureunittest35frameworka.png)

4. Użyj listy rozwijanej **platformy docelowej (wszystkie konfiguracje)** , aby zmienić platformę docelową na **.NET Framework 3,5** lub nowszą, jak pokazano w objaśnieniu B na poniższej ilustracji. Nie należy określać wersji klienta.

     ![Docelowa lista rozwijana platformy docelowej&#45;](../test/media/howtoconfigureunitest35frameworkstepb.png)

## <a name="retargeting-for-c-unit-test-projects"></a>Przekierowywanie dla projektów testów jednostkowych C#

1. Utwórz nowy projekt **projektu testów jednostkowych** C#.

2. W **Eksplorator rozwiązań**wybierz **Właściwości** z menu rozwijanego prawym przyciskiem myszy nowego projektu testu C#.

   Zostaną wyświetlone właściwości projektu testowego w języku C#.

3. Na karcie **aplikacja** wybierz pozycję **platforma docelowa**. Z listy rozwijanej wybierz **.NET Framework 3,5** lub nowszą wersję, jak pokazano na poniższej ilustracji. Nie należy określać wersji klienta.

   ![Docelowa lista rozwijana platformy docelowej&#45;](../test/media/howtoconfigureunittest35frameworkcsharp.png)

## <a name="retargeting-for-ccli-unit-test-projects"></a>Przekierowywanie dla projektów testów jednostkowych C++/CLI

1. Utwórz nowy projekt **projektu testów jednostkowych** języka C++.

   > [!WARNING]
   > Aby skompilować testy jednostkowe języka C++/CLI dla poprzedniej wersji programu .NET Framework dla Visual C++, należy użyć odpowiedniej wersji programu Visual Studio.

2. W **Eksplorator rozwiązań**wybierz pozycję **Zwolnij projekt** z nowego projektu testowego języka C++.

3. W **Eksplorator rozwiązań**wybierz niezaładowany projekt testowego języka C++, a następnie wybierz polecenie **Edytuj \<project name> . vcxproj**.

   Plik *. vcxproj* zostanie otwarty w edytorze.

4. Ustaw wartość w `TargetFrameworkVersion` wersji 3,5 lub nowszej w `PropertyGroup` etykiecie `"Globals"` . Nie należy określać wersji klienta:

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

5. Zapisz i zamknij plik *. vcxproj* .

6. W **Eksplorator rozwiązań**wybierz opcję Wybierz **Załaduj ponownie projekt** z menu rozwijanego prawym przyciskiem myszy nowego projektu testowego języka C++.

## <a name="see-also"></a>Zobacz też

- [Tworzenie rozwiązań SharePoint](../sharepoint/create-sharepoint-solutions.md)
- [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Okno dialogowe Zaawansowane ustawienia kompilatora (Visual Basic)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)
