---
title: Jak uruchomić program (C#)
description: Przewodnik początkującego dotyczący sposobu uruchamiania programu w języku C# w programie Visual Studio.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "81649638"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>Instrukcje: Uruchamianie programu w języku C# w programie Visual Studio

Co należy zrobić, aby uruchomić program, zależy od tego, jakiego typu program, aplikacja lub usługa jest, a także od tego, czy ma być uruchamiany w debugerze, czy nie. W najprostszym przypadku, gdy masz otwarty projekt w programie Visual Studio, skompiluj i uruchom go, naciskając klawisz **Ctrl** + **F5** (**Rozpocznij bez debugowania**) lub **F5** (**Rozpocznij od debugowania**) lub naciśnij zieloną strzałkę (**przycisk Start**) na głównym pasku narzędzi programu Visual Studio.

![Zrzut ekranu przedstawiający przycisk Start](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>Rozpoczynając od projektu

Jeśli masz projekt C# (plik *. csproj* ), możesz go uruchomić, jeśli jest to program możliwy do uruchomienia. Jeśli projekt zawiera plik C# z `Main` metodą, a jego wynik jest plikiem wykonywalnym (exe), najprawdopodobniej zostanie uruchomiony, jeśli kompilacja zostanie zakończona pomyślnie.

Jeśli masz już kod dla programu w projekcie w programie Visual Studio, Otwórz projekt. Aby otworzyć projekt, kliknij dwukrotnie lub naciśnij pozycję *csproj* w Eksploratorze plików systemu Windows lub z programu Visual Studio, wybierz **Otwórz projekt**, Przeglądaj, aby znaleźć plik projektu (*. csproj*), a następnie wybierz plik projektu.

Po załadowaniu projektów w programie Visual Studio naciśnij klawisz **Ctrl** + **F5** (**Rozpocznij bez debugowania**) lub użyj zielonego przycisku **Start** na pasku narzędzi programu Visual Studio, aby uruchomić program.  Jeśli istnieje wiele projektów, jeden z tą `Main` metodą musi być ustawiony jako projekt startowy. Aby ustawić projekt startowy, kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Ustaw jako projekt startowy**.

![Ustaw projekt startowy](media/set-as-startup-project.png)

Program Visual Studio próbuje skompilować i uruchomić projekt.  Jeśli występują błędy kompilacji, zobaczysz dane wyjściowe kompilacji w oknie **danych wyjściowych** i błędy w oknie **Lista błędów** .

Jeśli kompilacja zakończy się powodzeniem, aplikacja będzie działać w sposób właściwy dla typu projektu. Aplikacje konsolowe są uruchamiane w oknie terminalu, aplikacje klasyczne systemu Windows zaczynają się w nowym oknie, aplikacje sieci Web zaczynają się w przeglądarce (hostowanej przez IIS Express) itd.

## <a name="starting-from-code"></a>Rozpoczynanie od kodu

Jeśli zaczynasz od listy kodu, pliku kodu lub niewielkiej liczby plików, najpierw upewnij się, że kod, który chcesz uruchomić, pochodzi z zaufanego źródła i jest programem możliwy do uruchomienia. Jeśli ma `Main` metodę, prawdopodobnie jest to program możliwy do uruchomienia, którego można użyć w celu utworzenia projektu do pracy z nim w programie Visual Studio.

### <a name="code-listing-for-a-single-file"></a>Lista kodów dla pojedynczego pliku

Uruchom program Visual Studio, Otwórz pusty projekt konsoli języka C#, zaznacz cały kod w pliku CS, który znajduje się już w projekcie, i usuń go. Następnie wklej zawartość kodu do pliku CS. Gdy wkleisz kod, Zastąp lub Usuń kod, który był wcześniej. Zmień nazwę pliku, aby pasował do oryginalnego kodu.

### <a name="code-listings-for-a-few-files"></a>Fragmenty kodu dla kilku plików

Uruchom program Visual Studio, Otwórz pusty projekt konsoli języka C#, zaznacz cały kod w pliku CS, który znajduje się już w projekcie, i usuń go. Następnie wklej zawartość pierwszego pliku kodu do pliku CS. Zmień nazwę pliku, aby pasował do oryginalnego kodu. 

Dla drugiego pliku kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** , aby otworzyć menu skrótów dla projektu, a następnie wybierz polecenie **Dodaj > istniejący element** (lub użyj kombinacji klawiszy **SHIFT** + **Alt** + **a**) i wybierz pliki kodu.

### <a name="multiple-files-on-disk"></a>Wiele plików na dysku

1. Utwórz nowy projekt odpowiedniego typu (jeśli nie masz pewności, użyj **aplikacji konsolowej** C#).

2. Kliknij prawym przyciskiem myszy węzeł projektu, SE **Dodaj**  >  **istniejący element** , aby wybrać pliki i zaimportować je do projektu.  

### <a name="starting-from-a-folder"></a>Zaczynając od folderu

Podczas pracy z folderem wielu plików, najpierw sprawdź, czy istnieje projekt lub rozwiązanie.  Jeśli program został utworzony za pomocą programu Visual Studio, należy znaleźć plik projektu lub plik rozwiązania. Poszukaj plików z rozszerzeniem *csproj* lub SLN, a następnie w Eksploratorze plików systemu Windows kliknij dwukrotnie jeden z nich, aby otworzyć go w programie Visual Studio. Zobacz [Rozpoczynanie pracy z rozwiązania lub projektu programu Visual Studio](#starting-from-a-project).

Jeśli nie masz pliku projektu, na przykład jeśli kod został opracowany w innym środowisku programistycznym, a następnie otwórz folder najwyższego poziomu za pomocą metody **Open folder** w programie Visual Studio. Zobacz [Programowanie kodu bez projektów i rozwiązań](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="starting-from-a-github-or-azure-devops-repo"></a>Rozpoczynanie od repozytorium GitHub lub usługi Azure DevOps

Jeśli kod, który chcesz uruchomić, znajduje się w usłudze GitHub lub w repozytorium usługi Azure DevOps, możesz użyć programu Visual Studio, aby otworzyć projekt bezpośrednio z repozytorium. Zobacz [Otwieranie projektu z repozytorium](../tutorial-open-project-from-repo.md).

## <a name="run-the-program"></a>Uruchamianie programu

Aby uruchomić program, naciśnij zieloną strzałkę (przycisk**Start** ) na głównym pasku narzędzi programu Visual Studio lub naciśnij klawisz **F5** lub **Ctrl** + **F5** , aby uruchomić program. Gdy używasz przycisku **Start** , jest on uruchamiany w debugerze.  Program Visual Studio próbuje skompilować kod w projekcie i uruchomić go.  Jeśli to się powiedzie, świetnie! Ale jeśli nie, Kontynuuj odczytywanie niektórych pomysłów na temat pomyślnego skompilowania.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Kod może zawierać błędy, ale jeśli kod jest poprawny, ale tylko zależy od innych zestawów lub pakietów NuGet albo został zapisany w celu użycia innej wersji programu .NET, można łatwo rozwiązać ten problem.

### <a name="add-references"></a>Dodaj odwołania

Aby poprawnie skompilować kod, musi być poprawny i mieć odpowiednie odwołania skonfigurowane do bibliotek lub innych zależności. Można przyjrzeć się czerwonym wierszom falistej i w **Lista błędów** , aby sprawdzić, czy program zawiera błędy, nawet przed kompilacją i uruchomieniem. Jeśli widzisz błędy związane z nierozpoznanymi nazwami, prawdopodobnie musisz dodać odwołanie lub dyrektywę using albo oba te elementy. Jeśli kod odwołuje się do wszystkich zestawów lub pakietów NuGet, należy dodać te odwołania do projektu.

Program Visual Studio próbuje ułatwić zidentyfikowanie brakujących odwołań. Gdy nazwa jest nierozwiązana, w edytorze zostanie wyświetlona ikona żarówki. Jeśli klikniesz żarówkę, zobaczysz sugestie dotyczące sposobu rozwiązania problemu. Poprawki mogą być następujące:

- Dodaj dyrektywę using
- Dodaj odwołanie do zestawu lub
- Zainstaluj pakiet NuGet.

#### <a name="missing-using-directive"></a>Brak dyrektywy using

Na przykład na poniższym ekranie można wybrać opcję dodania `using System;` do początku pliku kodu w celu rozpoznania nierozpoznanej nazwy `Console` :

![Zrzut ekranu przedstawiający żarówkę, aby dodać dyrektywę using](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>Brak odwołania do zestawu

Odwołania platformy .NET mogą mieć postać zestawów lub pakietów NuGet. Zazwyczaj Jeśli znajdziesz kod źródłowy, Wydawca lub autor wyjaśni, jakie zestawy są wymagane i jakie pakiety zależy od kodu. Aby ręcznie dodać odwołanie do projektu, kliknij prawym przyciskiem myszy węzeł **odwołania** w **Eksplorator rozwiązań**, wybierz polecenie **Dodaj odwołanie**i Znajdź wymagany zestaw.

![Zrzut ekranu przedstawiający menu Dodaj odwołanie](media/add-reference.png)

Zestawy i Dodawanie odwołań można znaleźć, postępując zgodnie z instrukcjami w temacie [Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

#### <a name="missing-nuget-package"></a>Brak pakietu NuGet

Jeśli program Visual Studio wykryje brakujący pakiet NuGet, zostanie wyświetlona żarówka z opcją instalacji:

![Zrzut ekranu przedstawiający żarówkę do zainstalowania pakietu](media/lightbulb-add-package.png)

Jeśli to nie rozwiąże problemu, a program Visual Studio nie może zlokalizować pakietu, spróbuj wyszukać go w trybie online. Zobacz [Instalowanie i używanie pakietu NuGet w programie Visual Studio](/nuget/quickstart/install-and-use-a-package-in-visual-studio).

## <a name="use-the-right-version-of-net"></a>Użyj odpowiedniej wersji platformy .NET

Ponieważ różne wersje .NET Framework mają pewien stopień zgodności z poprzednimi wersjami, nowsza platforma może uruchamiać kod zapisany dla starszej struktury bez żadnych modyfikacji. Jednak czasami trzeba określić konkretną strukturę. Może być konieczne zainstalowanie określonej wersji .NET Framework lub .NET Core, jeśli nie została jeszcze zainstalowana. Zobacz [modyfikowanie programu Visual Studio](../../install/modify-visual-studio.md).

Aby zmienić platformę docelową, zobacz [zmiana platformy docelowej](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version). Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów .NET Framework określania błędów](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="next-steps"></a>Następne kroki

Poznaj środowisko programistyczne programu Visual Studio, odczytując [program Visual Studio IDE](../visual-studio-ide.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie pierwszej aplikacji C#](tutorial-console.md)
