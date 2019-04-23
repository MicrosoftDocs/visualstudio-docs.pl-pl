---
title: 'Instrukcje: Pomijanie ostrzeżeń kompilatora | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 27eeecc4330f772a2e1e8e065f927a8b17c03020
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60064313"
---
# <a name="how-to-suppress-compiler-warnings"></a>Instrukcje: Pomijanie ostrzeżeń kompilatora

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Declutter z dziennika kompilacji, określając jeden lub więcej rodzajów ostrzeżenia kompilatora, że nie ma on zawierać. Na przykład użyć tej techniki, aby przejrzeć niektóre, ale nie wszystkie informacje, które jest generowany automatycznie, gdy poziom szczegółowości dziennika kompilacji jest ustawiona na normalny, szczegółowe lub diagnostyki. Aby uzyskać więcej informacji na temat poziomu szczegółowości, zobacz [jak: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md).

### <a name="to-suppress-specific-warnings-for-visual-c-or-f"></a>Pomija określone ostrzeżenia dla wizualizacji C# lub F\#

1. W **Eksploratora rozwiązań**, wybierz projekt, w którym chcesz pominąć ostrzeżenia.

2. Na pasku menu wybierz **widoku**, **stron właściwości**.

3. Wybierz **kompilacji** strony.

4. W **pomijanie ostrzeżeń** Określ kody błędów, ostrzeżeń, które chcesz pominąć, oddzielone średnikami, a następnie ponownie skompiluj rozwiązanie.

### <a name="to-suppress-specific-warnings-for-visual-c"></a>Pomija określone ostrzeżenia dla języka Visual C++

1. W **Eksploratora rozwiązań**, wybierz projekt lub pliku, w którym chcesz pominąć ostrzeżenia źródła.

2. Na pasku menu wybierz **widoku**, **stron właściwości**.

3. Wybierz **właściwości konfiguracji** kategorii, wybierz **C/C++** kategorii, a następnie wybierz **zaawansowane** strony.

4. Wykonaj jedną z następujących czynności:

    - W **Wyłącz określone ostrzeżenia** Określ kody błędów, ostrzeżeń, które chcesz pominąć, rozdzielając je średnikiem.

    - W **Wyłącz określone ostrzeżenia** wybierz **Edytuj** Aby wyświetlić więcej opcji.

5. Wybierz **OK** przycisk, a następnie ponownie skompiluj rozwiązanie.

## <a name="suppressing-warnings-for-visual-basic"></a>Pomijanie ostrzeżeń dla języka Visual Basic

Aby ukryć określone ostrzeżenia kompilatora dla języka Visual Basic, edytowania pliku .vbproj dla projektu. Można również użyć [strona kompilowania, Projektant projektu](../ide/reference/compile-page-project-designer-visual-basic.md) pominąć ostrzeżenia według kategorii. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](../ide/configuring-warnings-in-visual-basic.md).

#### <a name="to-suppress-specific-warnings-for-visual-basic"></a>Pomija określone ostrzeżenia dla języka Visual Basic

1. W **Eksploratora rozwiązań**, wybierz projekt, w którym chcesz pominąć ostrzeżenia.

2. Na pasku menu wybierz **projektu**, **Zwolnij projekt**.

3. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **Edytuj**_ProjectName_**.vbproj**.

    Plik projektu jest otwarty w edytorze kodu.

4. Znajdź `<NoWarn></NoWarn>` element konfiguracji kompilacji, z którym tworzysz.

    W poniższym przykładzie przedstawiono `<NoWarn></NoWarn>` element pogrubioną czcionką dla konfiguracji kompilacji debugowania na x86 platformy:

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

5. Dodaj co najmniej jeden numery ostrzeżeń jako wartość `<NoWarn>` elementu. Jeśli określisz wiele numerów ostrzeżeń, oddziel je przecinkami, co ilustruje poniższy przykład.

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

6. Zapisz zmiany w pliku .vbproj.

7. Na pasku menu wybierz **projektu**, **Załaduj ponownie projekt**.

8. Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.

    **Dane wyjściowe** okna nie powoduje już zgłaszania ostrzeżeń, określonych przez użytkownika.

   Aby uzyskać więcej informacji, zobacz [/nowarn](http://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).

## <a name="see-also"></a>Zobacz też

- [Przewodnik: Kompilowanie aplikacji](../ide/walkthrough-building-an-application.md)
- [Instrukcje: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Kompilowanie i tworzenie](../ide/compiling-and-building-in-visual-studio.md)
