---
title: 'Instrukcje: pomijanie ostrzeżeń kompilatora | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aeb404c479edec5dec89f28e80584d435f5c370a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670642"
---
# <a name="how-to-suppress-compiler-warnings"></a>Porady: pomijanie ostrzeżeń kompilatora

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz wyrejestrować dziennik kompilacji, określając jeden lub więcej rodzajów ostrzeżeń kompilatora, które nie powinny zawierać. Można na przykład użyć tej techniki, aby przejrzeć niektóre, ale nie wszystkie informacje, które są generowane automatycznie podczas ustawiania szczegółowości dziennika kompilacji na normalne, szczegółowe lub diagnostyczne. Aby uzyskać więcej informacji na temat szczegółowości, zobacz [jak: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).

### <a name="to-suppress-specific-warnings-for-visual-c-or-f"></a>Aby pominąć określone ostrzeżenia dla wizualizacji C# lub F \#

1. W **Eksplorator rozwiązań**wybierz projekt, w którym mają zostać pominięte ostrzeżenia.

2. Na pasku menu wybierz **Widok**, **strony właściwości**.

3. Wybierz stronę **kompilacja** .

4. W polu **Pomiń ostrzeżenia** Określ kody błędów ostrzeżeń, które mają być pomijane, oddzielone średnikami, a następnie Skompiluj ponownie rozwiązanie.

### <a name="to-suppress-specific-warnings-for-visual-c"></a>Aby pominąć określone ostrzeżenia dla wizualizacjiC++

1. W **Eksplorator rozwiązań**wybierz projekt lub plik źródłowy, w którym mają zostać pominięte ostrzeżenia.

2. Na pasku menu wybierz **Widok**, **strony właściwości**.

3. Wybierz kategorię **Właściwości konfiguracji** , wybierz kategorię **CC++ /** , a następnie wybierz stronę **Zaawansowane** .

4. Wykonaj jedną z następujących czynności:

    - W polu **Wyłącz określone ostrzeżenia** Określ kody błędów ostrzeżeń, które mają zostać pominięte, oddzielone średnikami.

    - W polu **Wyłącz określone ostrzeżenia** wybierz pozycję **Edytuj** , aby wyświetlić więcej opcji.

5. Wybierz przycisk **OK** , a następnie Skompiluj ponownie rozwiązanie.

## <a name="suppressing-warnings-for-visual-basic"></a>Pomijanie ostrzeżeń dla Visual Basic

Można ukryć określone ostrzeżenia kompilatora dla Visual Basic, edytując plik vbproj dla projektu. Można również użyć [strony Kompilacja, Projektant projektu](../ide/reference/compile-page-project-designer-visual-basic.md) do pomijania ostrzeżeń według kategorii. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

#### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Aby pominąć określone ostrzeżenia dla Visual Basic

1. W **Eksplorator rozwiązań**wybierz projekt, w którym mają zostać pominięte ostrzeżenia.

2. Na pasku menu wybierz **projekt**, **Zwolnij projekt**.

3. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Edytuj**_ProjectName_ **. vbproj**.

    Plik projektu zostanie otwarty w edytorze kodu.

4. Znajdź element `<NoWarn></NoWarn>` w konfiguracji kompilacji, z którą tworzysz.

    Poniższy przykład pokazuje `<NoWarn></NoWarn>` element pogrubioną czcionką dla konfiguracji kompilacji debugowania na platformie x86:

   ```xml
   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">
       <PlatformTarget>x86</PlatformTarget>
       <DebugSymbols>true</DebugSymbols>
       <DebugType>full</DebugType>
       <Optimize>false</Optimize>
       <OutputPath>bin\Debug\</OutputPath>
       <DefineDebug>true</DefineDebug>
       <DefineTrace>true</DefineTrace>
       <ErrorReport>prompt</ErrorReport>
       <NoWarn></NoWarn>
       <WarningLevel>1</WarningLevel>
     </PropertyGroup>
   ```

5. Dodaj co najmniej jedną liczbę ostrzegawczą jako wartość elementu `<NoWarn>`. Jeśli określisz wiele numerów ostrzeżeń, rozdziel je przecinkami, jak pokazano w poniższym przykładzie.

   ```xml
   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">
       <PlatformTarget>x86</PlatformTarget>
       <DebugSymbols>true</DebugSymbols>
       <DebugType>full</DebugType>
       <Optimize>false</Optimize>
       <OutputPath>bin\Debug\</OutputPath>
       <DefineDebug>true</DefineDebug>
       <DefineTrace>true</DefineTrace>
       <ErrorReport>prompt</ErrorReport>
       <NoWarn>40059,42024</NoWarn>
       <WarningLevel>1</WarningLevel>
     </PropertyGroup>
   ```

6. Zapisz zmiany w pliku. vbproj.

7. Na pasku menu wybierz **projekt**, **Załaduj ponownie projekt**.

8. Na pasku menu wybierz **kompilacja**, **Skompiluj ponownie rozwiązanie**.

    W oknie **danych wyjściowych** nie są już wyświetlane ostrzeżenia, które zostały określone przez użytkownika.

   Aby uzyskać więcej informacji, zobacz [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).

## <a name="see-also"></a>Zobacz też

- [Przewodnik: Kompilowanie aplikacji](../ide/walkthrough-building-an-application.md)
- [Instrukcje: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Kompilowanie i tworzenie](../ide/compiling-and-building-in-visual-studio.md)
