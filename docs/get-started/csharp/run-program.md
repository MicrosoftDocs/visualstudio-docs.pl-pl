---
title: Jak uruchomić program (C#)
description: Przewodnik dla początkujących dotyczący sposobu uruchamiania programu w języku C# w Visual Studio.
ms.custom: vs-acquisition, get-started
ms.date: 10/16/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e20caabb55e65801224177168f5c936f81402bbd
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385230"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>How to: Run a C# program in Visual Studio

To, co należy zrobić, aby uruchomić program, zależy od tego, od czego rozpoczynasz, jakiego typu jest program, aplikacja lub usługa oraz od tego, czy chcesz uruchomić go w debugerze, czy nie. W najprostszym przypadku, gdy projekt jest otwarty w programie Visual Studio, skompilować i uruchomić go, naciskając klawisze **Ctrl** F5 (Rozpocznij bez debugowania) lub F5 (Rozpocznij od debugowania) lub naciśnij zieloną strzałkę +  **(Przycisk** startowy)  na głównym pasku Visual Studio narzędzi.

![Zrzut ekranu przedstawiający przycisk Uruchamiania](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>Rozpoczynanie od projektu

Jeśli masz projekt w języku C#*(plik csproj),* możesz go uruchomić, jeśli jest to program uruchamiany. Jeśli projekt zawiera plik C# z metodą , a jego dane wyjściowe to plik wykonywalny (EXE), najprawdopodobniej zostanie on uruchomiony, jeśli `Main` kompilacja przebiegnie pomyślnie.

Jeśli masz już kod programu w projekcie w Visual Studio, otwórz projekt. Aby otworzyć projekt, kliknij dwukrotnie lub naciśnij plik *csproj* z witryny Windows Eksplorator plików lub z witryny Visual Studio, wybierz pozycję Otwórz **projekt,** przejdź do pliku projektu *(csproj)* i wybierz plik projektu.

Po zakończeniu ładowania projektów w Visual Studio naciśnij klawisz **Ctrl** + **F5** (Uruchom bez debugowania) lub użyj zielonego przycisku **Start** Visual Studiopasku narzędzi, aby uruchomić program.  Jeśli istnieje wiele projektów, ten z metodą musi być ustawiony `Main` jako projekt startowy. Aby ustawić projekt startowy, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Ustaw jako projekt startowy**.

![Ustawianie projektu startowego](media/set-as-startup-project.png)

Visual Studio próbuje skompilować i uruchomić projekt.  Jeśli występują błędy kompilacji, dane  wyjściowe kompilacji zostaną wyświetlony w oknie Dane wyjściowe, a błędy w **oknie Lista** błędów.

Jeśli kompilacja zakończy się pomyślnie, aplikacja będzie uruchamiana w sposób odpowiedni dla typu projektu. Aplikacje konsolowe działają w oknie terminalu, aplikacje klasyczne systemu Windows są uruchamiane w nowym oknie, aplikacje internetowe są uruchamiane w przeglądarce (hostowanej przez IIS Express) i tak dalej.

## <a name="starting-from-code"></a>Rozpoczynanie od kodu

Jeśli rozpoczynasz od listy kodu, pliku kodu lub niewielkiej liczby plików, najpierw upewnij się, że kod, który chcesz uruchomić, pochodzi z zaufanego źródła i jest programem uruchamianym. Jeśli ma metodę , prawdopodobnie jest przeznaczony jako program do uruchamiania, za pomocą szablonu aplikacja konsolowa można utworzyć projekt do pracy z nim w `Main` Visual Studio.

### <a name="code-listing-for-a-single-file"></a>Lista kodu dla pojedynczego pliku

Uruchom Visual Studio, otwórz pusty projekt konsoli języka C#, wybierz cały kod w pliku cs, który już istnieje w projekcie, i usuń go. Następnie wklej zawartość kodu do pliku cs. Po wklejeniu kodu zastąp lub usuń kod, który był tam wcześniej. Zmień nazwę pliku, aby był zgodne z oryginalnym kodem.

### <a name="code-listings-for-a-few-files"></a>Listy kodu dla kilku plików

Uruchom Visual Studio, otwórz pusty projekt konsoli języka C#, wybierz cały kod w pliku cs, który już istnieje w projekcie, i usuń go. Następnie wklej zawartość pierwszego pliku kodu do pliku cs. Zmień nazwę pliku, aby był zgodne z oryginalnym kodem. 

W przypadku drugiego pliku kliknij prawym przyciskiem myszy węzeł projektu w programie **Eksplorator rozwiązań, aby** otworzyć menu skrótów projektu, a następnie wybierz polecenie **Dodaj istniejący** element > (lub użyj kombinacji klawiszy **Shift** + **Alt** + **A),** a następnie wybierz pliki kodu.

### <a name="multiple-files-on-disk"></a>Wiele plików na dysku

1. Utwórz nowy projekt odpowiedniego typu (jeśli nie masz pewności, użyj aplikacji konsolowej C#). 

2. Kliknij prawym przyciskiem myszy węzeł projektu, a następnie pozycję **Dodaj** istniejący  >  **element,** aby wybrać pliki i zaimportować je do projektu.  

### <a name="starting-from-a-folder"></a>Uruchamianie z folderu

Podczas pracy z folderem z wieloma plikami najpierw sprawdź, czy istnieje projekt lub rozwiązanie.  Jeśli program został utworzony za Visual Studio, powinien znaleźć plik projektu lub plik rozwiązania. Poszukaj plików z rozszerzeniem *csproj* lub rozszerzeniem sln, a następnie na stronie windows Eksplorator plików kliknij dwukrotnie jeden z nich, aby otworzyć je w Visual Studio. Zobacz Starting from a Visual Studio solution or project (Rozpoczynanie od [Visual Studio rozwiązania lub projektu).](#starting-from-a-project)

Jeśli nie masz pliku projektu, na przykład jeśli kod został opracowany w innym środowisku projektowym, otwórz folder najwyższego poziomu przy użyciu metody Otwórz folder w programie Visual Studio.  Zobacz [Develop code without projects or solutions (Tworzenie](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)kodu bez projektów i rozwiązań).

## <a name="starting-from-a-github-or-azure-devops-repo"></a>Rozpoczynanie pracy z repozytorium GitHub Azure DevOps repozytorium

Jeśli kod, który chcesz uruchomić, znajduje się w usłudze GitHub lub Azure DevOps repozytorium, możesz użyć polecenia Visual Studio, aby otworzyć projekt bezpośrednio z repozytorium. Zobacz [Open a project from a repo (Otwieranie projektu z repo).](../tutorial-open-project-from-repo.md)

## <a name="run-the-program"></a>Uruchamianie programu

Aby uruchomić program, naciśnij zieloną strzałkę **(przycisk Start)** na głównym pasku Visual Studio narzędziu lub naciśnij **klawisz F5** lub **Ctrl** + **F5,** aby uruchomić program. Gdy używasz **przycisku Start,** jest on uruchamiany w debugerze.  Visual Studio próbuje skompilować kod w projekcie i uruchomić go.  Jeśli to się powiedzie, świetnie! Jeśli jednak nie, czytaj dalej, aby uzyskać kilka pomysłów na pomyślne skompilowanie aplikacji.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Kod może zawierać błędy, ale jeśli kod jest poprawny, ale zależy tylko od innych zestawów lub pakietów NuGet albo został napisany do innej wersji programu .NET, można go łatwo naprawić.

### <a name="add-references"></a>Dodawanie odwołań

Aby kod został poprawnie skompilowany, musi być poprawny i mieć skonfigurowane odpowiednie odwołania do bibliotek lub innych zależności. Możesz przyjrzeć się czerwonym liniami zquiggly i na liście błędów, aby sprawdzić, czy program zawiera jakiekolwiek błędy, nawet przed skompilowanie i uruchomienie.  Jeśli występują błędy związane z nierozpoznaną nazwami, prawdopodobnie musisz dodać odwołanie, dyrektywę using lub obie te właściwości. Jeśli kod odwołuje się do jakichkolwiek zestawów lub pakietów NuGet, należy dodać te odwołania w projekcie.

Visual Studio próbuje zidentyfikować brakujące odwołania. Gdy nazwa nie zostanie rozwiązana, w edytorze zostanie wyświetlona ikona żarówki. Jeśli klikniesz żarówkę, zobaczysz sugestie dotyczące sposobu rozwiązania problemu. Poprawki mogą być:

- dodawanie dyrektywy using
- dodawanie odwołania do zestawu lub
- zainstaluj pakiet NuGet.

#### <a name="missing-using-directive"></a>Brak dyrektywy using

Na przykład na poniższym ekranie można dodać do początku pliku kodu, aby rozpoznać `using System;` nierozpoznaną nazwę `Console` :

![Zrzut ekranu przedstawiający żarówkę w celu dodania dyrektywy using](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>Brak odwołania do zestawu

Odwołania do .NET mogą mieć postać zestawów lub pakietów NuGet. Zwykle w przypadku znalezienia kodu źródłowego wydawca lub autor wyjaśni, od jakich zestawów i od jakich pakietów zależy kod. Aby ręcznie dodać odwołanie do projektu, kliknij  prawym przyciskiem myszy węzeł **Odwołania** w menu Eksplorator rozwiązań , wybierz polecenie Dodaj odwołanie **i** znajdź wymagany zestaw.

![Zrzut ekranu przedstawiający menu Dodaj odwołanie](media/add-reference.png)

Zestawy i odwołania można znaleźć, korzystając z instrukcji w tece Dodawanie lub usuwanie odwołań [za pomocą menedżera odwołań](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

#### <a name="missing-nuget-package"></a>Brak pakietu NuGet

Jeśli Visual Studio wykryje brakujący pakiet NuGet, zostanie wyświetlona żarówka z opcją jego zainstalowania:

![Zrzut ekranu przedstawiający żarówkę w celu zainstalowania pakietu](media/lightbulb-add-package.png)

Jeśli to nie rozwiąże problemu i Visual Studio nie będzie można zlokalizować pakietu, spróbuj wyszukać go w trybie online. Zobacz [Instalowanie i używanie pakietu NuGet w Visual Studio](/nuget/quickstart/install-and-use-a-package-in-visual-studio).

## <a name="use-the-right-version-of-net"></a>Używanie odpowiedniej wersji programu .NET

Ze względu na to, że różne wersje .NET Framework mają pewien stopień zgodności z poprzednimi wersjami, nowsze struktury mogą uruchamiać kod napisany dla starszej struktury bez żadnych modyfikacji. Czasami jednak konieczne jest ukierunkowanie określonej struktury. Może być konieczne zainstalowanie określonej wersji programu .NET Framework lub .NET Core, jeśli nie została jeszcze zainstalowana. Zobacz [Modyfikowanie Visual Studio](../../install/modify-visual-studio.md).

Aby zmienić platformę docelową, zobacz [Zmienianie docelowej struktury](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version). Aby uzyskać więcej informacji, zobacz Troubleshooting .NET Framework targeting errors (Rozwiązywanie problemów z błędami [określania wartości docelowej).](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)

## <a name="next-steps"></a>Następne kroki

Zapoznaj się z Visual Studio środowiska projektowego, czytając [temat Welcome to the Visual Studio IDE](../visual-studio-ide.md)(Środowisko IDE aplikacji Visual Studio ).

## <a name="see-also"></a>Zobacz też

[Tworzenie pierwszej aplikacji C#](tutorial-console.md)
