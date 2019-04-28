---
title: Testy jednostkowe docelowe wcześniejszej wersji programu .NET Framework
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
author: gewarren
ms.openlocfilehash: 0d77bd4fa5a1797b5e405c0b1af12cd1c24b18f7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979387"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Instrukcje: Konfigurowanie testów jednostkowych pod kątem starszej wersji programu .NET Framework

Po utworzeniu projektu testu w programie Microsoft Visual Studio najnowszą wersję programu .NET Framework jest domyślnie jako cel. Ponadto jeśli zaktualizujesz projekty testowe z poprzednich wersji programu Visual Studio, ich uaktualnienia pod kątem najbardziej aktualną wersję programu .NET Framework. Edytując właściwości projektu, można jawnie ponownie docelowych projektu we wcześniejszych wersjach programu .NET Framework.

Jednostki można tworzyć projekty testowe, przeznaczonych dla określonej wersji programu .NET Framework. Docelowa wersja musi być w wersji 3.5 lub nowszej, a nie może być wersji klienta. Program Visual Studio umożliwia następujące podstawowa pomoc techniczna dla testów jednostkowych, przeznaczonych dla określonych wersji:

- Można tworzyć projektów testów jednostkowych i określania elementów docelowych widoków do określonej wersji programu .NET Framework.

- Można uruchomić testów jednostkowych przeznaczonych określonej wersji programu .NET Framework w programie Visual Studio na komputerze lokalnym.

- Można uruchomić testy jednostkowe, przeznaczonych dla określonej wersji programu .NET Framework za pomocą *MSTest.exe* w wierszu polecenia.

- Możesz uruchomić testy jednostkowe na agencie kompilacji jako część kompilacji.

**Testowanie aplikacji SharePoint**

Funkcje wymienione powyżej również umożliwiają pisanie testów jednostkowych i testów integracji aplikacji programu SharePoint przy użyciu programu Visual Studio. Aby uzyskać więcej informacji na temat programowania aplikacji programu SharePoint przy użyciu programu Visual Studio, zobacz [rozwiązań SharePoint Utwórz](../sharepoint/create-sharepoint-solutions.md), [kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md) i [upewnij się, jak i debugowania Kod programu SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md).

**Ograniczenia**

Poniższe ograniczenia mają zastosowanie, gdy miejscem docelowym ponownie swoje projekty testów, aby używać starszych wersji programu .NET Framework:

- W .NET Framework 3.5 wielowersyjności kodu w programie jest obsługiwana dla projektów testowych, zawierające testy jednostkowe tylko. .NET Framework 3.5 nie obsługuje inny typ testu, takie jak kodowane testy interfejsu użytkownika lub obciążenia. Ponownie wartości docelowej jest zablokowana dla typów testów niż testy jednostkowe.

- Wykonywanie testów, które są przeznaczone dla starszej wersji programu .NET Framework jest obsługiwany tylko w przypadku domyślnego adaptera hosta. Nie jest obsługiwana na karcie hosta ASP.NET. Aplikacje ASP.NET, które są uruchamiane w kontekście ASP.NET Development Server muszą być zgodne z bieżącą wersją programu .NET Framework.

- Obsługa zbierania danych jest wyłączone, po uruchomieniu testów, które obsługują wielowersyjności kodu w programie .NET Framework 3.5. Możesz uruchomić pokrycie kodu za pomocą narzędzia wiersza polecenia programu Visual Studio.

- Testy jednostkowe, które używają .NET Framework 3.5 nie można uruchomić na komputerze zdalnym.

- Testy jednostkowe do wcześniejszych wersji klienta w ramach nie może być przeznaczony.

## <a name="retargeting-for-visual-basic-unit-test-projects"></a>Trwa przekierowywanie do projektów testów jednostkowych dla języka Visual Basic

1. Utwórz nowego języka Visual Basic **projektu testu jednostkowego** projektu.

2. W **Eksploratora rozwiązań**, wybierz **właściwości** z menu kliknij prawym przyciskiem myszy nowy projekt testowy Visual Basic.

     Wyświetlane są właściwości dla projektu testowego programu Visual Basic.

3. Na **skompilować** kartę, wybrać **zaawansowane opcje kompilacji** jak pokazano na poniższej ilustracji.

     ![Zaawansowane opcje kompilacji](../test/media/howtoconfigureunittest35frameworka.png)

4. Użyj **platformy docelowej (wszystkie konfiguracje)** listy rozwijanej, aby zmienić platformę docelową, aby **.NET Framework 3.5** lub nowszy, zgodnie z objaśnieniem B na poniższej ilustracji. Nie należy określać wersję klienta.

     ![TARGET framework listy&#45;listy rozwijanej](../test/media/howtoconfigureunitest35frameworkstepb.png)

## <a name="retargeting-for-c-unit-test-projects"></a>Trwa przekierowywanie do C# projektów testów jednostkowych

1. Utwórz nową C# **projektu testu jednostkowego** projektu.

2. W **Eksploratora rozwiązań**, wybierz **właściwości** do menu kliknij prawym przyciskiem myszy nową C# projektu testowego.

   Właściwości usługi C# projektu testowego są wyświetlane.

3. Na **aplikacji** kartę, wybrać **platformę docelową**. Z listy rozwijanej wybierz **.NET Framework 3.5** lub nowszej wersji, jak pokazano na poniższej ilustracji. Nie należy określać wersję klienta.

   ![TARGET framework listy&#45;listy rozwijanej](../test/media/howtoconfigureunittest35frameworkcsharp.png)

## <a name="retargeting-for-ccli-unit-test-projects"></a>Trwa przekierowywanie do C++/projektów testów jednostkowych interfejsu wiersza polecenia

1. Tworzenie nowego C++ **projektu testu jednostkowego** projektu.

   > [!WARNING]
   > Aby zbudować C + +/ testów jednostkowych interfejsu wiersza polecenia dla wcześniejszych wersji programu .NET framework dla Visual C++, należy użyć odpowiedniej wersji programu Visual Studio.

2. W **Eksploratora rozwiązań**, wybierz **Zwolnij projekt** z projektu testu języka C++.

3. W **Eksploratora rozwiązań**, wybierz zwolnionego projektu testu języka C++, a następnie wybierz **Edytuj \<Nazwa projektu > .vcxproj**.

   *.Vcxproj* plik zostanie otwarty w edytorze.

4. Ustaw `TargetFrameworkVersion` w wersji 3.5 lub nowszej wersji w `PropertyGroup` etykietą `"Globals"`. Nie należy określać wersja klienta:

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

5. Zapisz i Zamknij *.vcxproj* pliku.

6. W **Eksploratora rozwiązań**, wybierz Zaznacz **Załaduj ponownie projekt** z menu kliknij prawym przyciskiem myszy nowy projekt testów języka C++.

## <a name="see-also"></a>Zobacz także

- [Tworzenie rozwiązań SharePoint](../sharepoint/create-sharepoint-solutions.md)
- [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Okno dialogowe Ustawienia zaawansowane kompilatora (Visual Basic)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)
