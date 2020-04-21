---
title: Jak uruchomić program (C#)
description: Przewodnik dla początkujących, jak uruchomić program C# w programie Visual Studio.
ms.custom: get-started
ms.date: 10/16/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ee28bde6de10006ccfdc5175cca629ad9d1590d0
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649638"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Jak: Uruchamianie programu języka C# w programie Visual Studio

Co należy zrobić, aby uruchomić program zależy od tego, od czego zaczynasz, jaki typ programu, aplikacji lub usługi jest i czy chcesz go uruchomić w debugerze, czy nie. W najprostszym przypadku, gdy masz projekt otwarty w programie Visual Studio, skompiluj i uruchom go, naciskając **klawisze Ctrl**+**F5** **(Start bez debugowania)** lub **F5** (**Start z debugowaniem)** lub naciśnij zieloną strzałkę ( Przycisk**Start**) na głównym pasku narzędzi programu Visual Studio.

![Zrzut ekranu przedstawiający przycisk start](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>Począwszy od projektu

Jeśli masz projekt języka C# (plik*csproj),* możesz go uruchomić, jeśli jest to program do uruchomienia. Jeśli projekt zawiera plik Języka `Main` C# z metodą, a jego dane wyjściowe jest wykonywalny (EXE), a następnie najprawdopodobniej zostanie uruchomiony, jeśli zostanie pomyślnie zbudowany.

Jeśli masz już kod programu w projekcie w programie Visual Studio, otwórz projekt. Aby otworzyć projekt, kliknij dwukrotnie plik *csproj lub csproj* z Eksploratora plików systemu Windows lub w programie Visual Studio, wybierz pozycję Otwórz **projekt**, przejdź do pliku projektu (*csproj*) i wybierz plik projektu.

Po załadowaniu projektów w programie Visual Studio naciśnij klawisz **Ctrl**+**F5** **(Start bez debugowania)** lub użyj zielonego przycisku **Start** na pasku narzędzi Visual Studio, aby uruchomić program.  Jeśli istnieje wiele projektów, ten `Main` z metodą musi być ustawiony jako projekt startowy. Aby ustawić projekt startowy, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Ustaw jako projekt startowy**.

![Ustawianie projektu uruchamiania](media/set-as-startup-project.png)

Visual Studio próbuje skompilować i uruchomić projekt.  Jeśli występują błędy kompilacji, zobaczysz dane wyjściowe kompilacji w oknie **Dane wyjściowe** i błędy w oknie **Lista błędów.**

Jeśli kompilacja powiedzie się, aplikacja działa w sposób, który jest odpowiedni dla typu projektu. Aplikacje konsoli działają w oknie terminala, aplikacje klasyczne systemu Windows rozpoczynają się w nowym oknie, aplikacje internetowe uruchamiają się w przeglądarce (hostowane przez usługi IIS Express) i tak dalej.

## <a name="starting-from-code"></a>Począwszy od kodu

Jeśli zaczynasz od listy kodu, pliku kodu lub niewielkiej liczby plików, najpierw upewnij się, że kod, który chcesz uruchomić, pochodzi z zaufanego źródła i jest programem do uruchomienia. Jeśli ma `Main` metodę, prawdopodobnie jest przeznaczony jako program do uruchomienia, który można użyć szablonu aplikacji konsoli do utworzenia projektu do pracy z nim w programie Visual Studio.

### <a name="code-listing-for-a-single-file"></a>Lista kodów dla pojedynczego pliku

Uruchom program Visual Studio, otwórz pusty projekt konsoli Języka C#, wybierz cały kod w pliku cs, który jest już w projekcie, i usuń go. Następnie wklej zawartość kodu do pliku cs. Podczas wklejania kodu, zastąpić lub usunąć kod, który był tam wcześniej. Zmień nazwę pliku, aby dopasować go do oryginalnego kodu.

### <a name="code-listings-for-a-few-files"></a>Lista kodów dla kilku plików

Uruchom program Visual Studio, otwórz pusty projekt konsoli Języka C#, wybierz cały kod w pliku cs, który jest już w projekcie, i usuń go. Następnie wklej zawartość pierwszego pliku kodu do pliku cs. Zmień nazwę pliku, aby dopasować go do oryginalnego kodu. 

W przypadku drugiego pliku kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań,** aby otworzyć menu skrótów dla projektu, a następnie wybierz polecenie **Dodaj > istniejący element** (lub użyj kombinacji klawiszy **Shift**+**Alt**+**A)** i wybierz pliki kodu.

### <a name="multiple-files-on-disk"></a>Wiele plików na dysku

1. Utwórz nowy projekt o odpowiednim typie (użyj **aplikacji konsoli** W języku C#, jeśli nie masz pewności).

2. Kliknij prawym przyciskiem myszy węzeł projektu, se **Dodaj** > **istniejący element,** aby wybrać pliki i zaimportować je do projektu.  

### <a name="starting-from-a-folder"></a>Uruchamianie z folderu

Podczas pracy z folderem wielu plików, najpierw sprawdź, czy istnieje projekt lub rozwiązanie.  Jeśli program został utworzony za pomocą programu Visual Studio, należy znaleźć plik projektu lub plik rozwiązania. Poszukaj plików z rozszerzeniem *.csproj* lub .sln, a w Eksploratorze plików Windows kliknij dwukrotnie jeden z nich, aby otworzyć je w programie Visual Studio. Zobacz [Uruchamianie z rozwiązania lub projektu programu Visual Studio.](#starting-from-a-project)

Jeśli nie masz pliku projektu, na przykład jeśli kod został opracowany w innym środowisku programistycznym, a następnie otwórz folder najwyższego poziomu przy użyciu open **folder** metody w programie Visual Studio. Zobacz [Tworzenie kodu bez projektów i rozwiązań](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="starting-from-a-github-or-azure-devops-repo"></a>Uruchamianie repozytorium GitHub lub Usługi Azure DevOps

Jeśli kod, który chcesz uruchomić znajduje się w usłudze GitHub lub w repozytorium usługi Azure DevOps, można użyć programu Visual Studio, aby otworzyć projekt bezpośrednio z repozytorium. Zobacz [Otwieranie projektu z repozytorium](../tutorial-open-project-from-repo.md).

## <a name="run-the-program"></a>Uruchamianie programu

Aby uruchomić program, naciśnij zieloną strzałkę (przycisk**Start)** na głównym pasku narzędzi programu Visual Studio lub naciśnij **klawiszE F5** lub **Ctrl**+**F5,** aby uruchomić program. Podczas korzystania z przycisku **Start,** działa pod debugerem.  Visual Studio próbuje skompilować kod w projekcie i uruchomić go.  Jeśli to się uda, świetnie! Ale jeśli nie, kontynuuj czytanie dla niektórych pomysłów, jak go zbudować pomyślnie.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Kod może mieć błędy, ale jeśli kod jest poprawny, ale po prostu zależy od niektórych innych zestawów lub pakietów NuGet lub został napisany w celu kierowania innej wersji .NET, może być w stanie łatwo go naprawić.

### <a name="add-references"></a>Dodawanie odwołań

Aby utworzyć poprawnie, kod musi być poprawny i mieć odpowiednie odwołania skonfigurowane do bibliotek lub innych zależności. Możesz spojrzeć na czerwone linie faliste i na **liście błędów,** aby sprawdzić, czy program ma jakieś błędy, nawet przed skompilować i uruchomić go. Jeśli widzisz błędy związane z nierozwiązanymi nazwami, prawdopodobnie musisz dodać odwołanie lub using dyrektywy lub obu. Jeśli kod odwołuje się do wszystkich zestawów lub pakietów NuGet, należy dodać te odwołania w projekcie.

Visual Studio próbuje pomóc zidentyfikować brakujące odwołania. Gdy nazwa nie zostanie rozpoznana, w edytorze pojawi się ikona żarówki. Po kliknięciu żarówki możesz zobaczyć kilka sugestii, jak rozwiązać problem. Poprawki mogą być:

- dodawanie using dyrektywy
- dodać odniesienie do zestawu, lub
- zainstalować pakiet NuGet.

#### <a name="missing-using-directive"></a>Brak użycia dyrektywy

Na przykład na poniższym ekranie można `using System;` dodać do początku pliku kodu, aby `Console`rozpoznać nierozwiązaną nazwę:

![Zrzut ekranu przedstawiający żarówkę w celu dodania dyrektywy o użyciu](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>Brak odwołania do złożenia

Odwołania .NET mogą mieć postać zestawów lub pakietów NuGet. Zazwyczaj, jeśli znajdziesz kod źródłowy, wydawca lub autor wyjaśni, jakie zestawy są wymagane i jakie pakiety zależy od kodu. Aby ręcznie dodać odwołanie do projektu, kliknij prawym przyciskiem myszy węzeł **Odwołania** w **Eksploratorze rozwiązań**, wybierz pozycję **Dodaj odwołanie**i znajdź wymagany zestaw.

![Zrzut ekranu przedstawiający menu Dodaj odwołanie](media/add-reference.png)

Można znaleźć zestawy i dodać odwołania, postępując zgodnie z instrukcjami w [Dodaj lub usuń odwołania za pomocą menedżera odwołań](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

#### <a name="missing-nuget-package"></a>Brak pakietu NuGet

Jeśli program Visual Studio wykryje brakujący pakiet NuGet, pojawi się żarówka i daje możliwość zainstalowania go:

![Zrzut ekranu przedstawiający żarówkę do zainstalowania pakietu](media/lightbulb-add-package.png)

Jeśli to nie rozwiąże problemu i visual studio nie może zlokalizować pakiet, spróbuj wyszukać go w trybie online. Zobacz [Instalowanie i używanie pakietu NuGet w programie Visual Studio.](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

## <a name="use-the-right-version-of-net"></a>Użyj odpowiedniej wersji platformy .NET

Ponieważ różne wersje programu .NET Framework mają pewien stopień zgodności z powrotem, nowsza struktura może uruchomić kod napisany dla starszej struktury bez żadnych modyfikacji. Ale czasami trzeba kierować określone ramy. Może być konieczne zainstalowanie określonej wersji programu .NET Framework lub .NET Core, jeśli nie jest jeszcze zainstalowana. Zobacz [Modyfikowanie programu Visual Studio](../../install/modify-visual-studio.md).

Aby zmienić platformę docelową, zobacz [Zmienianie struktury docelowej](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version). Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z błędami kierowania programu .NET Framework](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="next-steps"></a>Następne kroki

Eksploruj środowisko programistyczne Programu Visual Studio, czytając [program "Powitaj w środowisku IDE programu Visual Studio".](../visual-studio-ide.md)

## <a name="see-also"></a>Zobacz też

[Tworzenie pierwszej aplikacji w języku C#](tutorial-console.md)
