---
title: Opracowywanie kodu bez projektów i rozwiązań
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a88bfb5f12ae707c98eedd1f57a4be14665aa83c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652502"
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Programowanie kodu w programie Visual Studio bez projektów i rozwiązań

Możesz otworzyć kod z niemal dowolnego typu projektu opartego na katalogu w programie Visual Studio bez konieczności stosowania rozwiązania lub pliku projektu. Oznacza to, że można na przykład klonować repozytorium w usłudze GitHub, otwierać je bezpośrednio w programie Visual Studio i zacząć opracowywać, bez konieczności tworzenia rozwiązania lub projektu. W razie konieczności można określić niestandardowe zadania kompilacji i parametry uruchamiania za poorednictwem prostych plików JSON.

Po otwarciu plików kodu w programie Visual Studio **Eksplorator rozwiązań** wyświetla wszystkie pliki w folderze. Możesz kliknąć dowolny plik, aby rozpocząć jego edytowanie. W tle program Visual Studio uruchamia indeksowanie plików w celu włączenia funkcji IntelliSense, nawigowania i refaktoryzacji. Podczas edytowania, tworzenia, przenoszenia lub usuwania plików program Visual Studio automatycznie śledzi zmiany i ciągle aktualizuje swój indeks IntelliSense. Kod będzie wyglądać ze kolorem składni i, w wielu przypadkach, uwzględniać podstawowe uzupełnianie instrukcji IntelliSense.

## <a name="open-any-code"></a>Otwórz dowolny kod

Możesz otworzyć kod w programie Visual Studio w dowolny z następujących sposobów:

- Na pasku menu programu Visual Studio wybierz pozycję **plik**  > **Otwórz**  > **folder**, a następnie przejdź do lokalizacji kodu.

- W menu kontekstowym (kliknij prawym przyciskiem myszy) folderu zawierającego kod wybierz polecenie **Otwórz w programie Visual Studio** .

::: moniker range="vs-2017"
- Wybierz link **Otwórz folder** na **stronie startowej**programu Visual Studio.
::: moniker-end

::: moniker range=">=vs-2019"
- Wybierz link **Otwórz folder** w oknie uruchamiania.
::: moniker-end

- Jeśli jesteś użytkownikiem z klawiatury, naciśnij klawisz **Ctrl** +**Shift** +**Alt** +**O** w programie Visual Studio.

- Otwórz kod ze sklonowanego repozytorium GitHub.

### <a name="to-open-code-from-a-cloned-github-repo"></a>Aby otworzyć kod ze sklonowanego repozytorium GitHub

Poniższy przykład pokazuje, jak sklonować repozytorium GitHub, a następnie otworzyć jego kod w programie Visual Studio. Aby wykonać tę procedurę, musisz mieć konto usługi GitHub i narzędzie git dla systemu Windows zainstalowane w systemie. Aby uzyskać więcej informacji, zobacz [Tworzenie nowego konta usługi GitHub](https://help.github.com/articles/signing-up-for-a-new-github-account/) i [git dla systemu Windows](https://git-for-windows.github.io/) .

1. Przejdź do repozytorium, które chcesz sklonować w serwisie GitHub.

1. Wybierz przycisk **Klonuj lub Pobierz** , a następnie wybierz przycisk **Kopiuj do schowka** w menu rozwijanym, aby skopiować bezpieczny adres URL repozytorium GitHub.

   ![Przycisk klonowania GitHub](./media/VSIDE_Code_Clone.png)

1. W programie Visual Studio wybierz kartę **Team Explorer** , aby otworzyć **Team Explorer**. Jeśli nie widzisz karty, otwórz ją z **widoku**  > **Team Explorer**.

1. W Team Explorer w sekcji **lokalne repozytoria Git** wybierz polecenie **klonowania** , a następnie wklej adres URL strony GitHub do pola tekstowego.

   ![Klonowanie projektu](./media/VSIDE_Code_Clone2.png)

1. Wybierz przycisk **klon** , aby sklonować pliki projektu do lokalnego repozytorium git. W zależności od rozmiaru repozytorium ten proces może potrwać kilka minut.

1. Po sklonowaniu repozytorium do systemu w obszarze **Team Explorer**wybierz polecenie **Otwórz** w menu kontekstowym (kliknij prawym przyciskiem myszy) dla nowo sklonowanego repozytorium.

   ![Sklonowane repozytorium](./media/VSIDE_Code_Clone3.png)

1. Wybierz polecenie **Pokaż widok folderu** , aby wyświetlić pliki w **Eksplorator rozwiązań**.

   ![Pokaż widok folderu](./media/VSIDE_Code_Clone3_show.png)

   Teraz można przeglądać foldery i pliki w sklonowanym repozytorium, a także wyświetlać i przeszukiwać kod w edytorze kodu programu Visual Studio, dokończc z kolorem składni i innymi funkcjami.

## <a name="run-and-debug-your-code"></a>Uruchamianie i debugowanie kodu

Możesz debugować kod w programie Visual Studio bez projektu lub rozwiązania. Aby debugować niektóre Języki, może być konieczne określenie prawidłowego *pliku startowego* w bazie kodu, takiej jak skrypt, plik wykonywalny lub projekt. Pole listy rozwijanej obok przycisku **Start** na pasku narzędzi zawiera wszystkie elementy startowe wykryte przez program Visual Studio, a także elementy, które zostały wyznaczone. Program Visual Studio uruchamia ten kod jako pierwszy podczas debugowania kodu.

Konfigurowanie kodu do uruchamiania w programie Visual Studio różni się w zależności od rodzaju kodu i narzędzi kompilacji.

### <a name="codebases-that-use-msbuild"></a>Bazy kodu używające MSBuild

Bazy kodu oparte na programie MSBuild mogą mieć wiele konfiguracji kompilacji, które pojawiają się na liście rozwijanej przycisku **Start** . Wybierz plik, który ma być używany jako element startowy, a następnie wybierz przycisk **Start** , aby rozpocząć debugowanie.

> [!NOTE]
> W C# przypadku baz kodu i Visual Basic, musisz mieć zainstalowane obciążenie **Programowanie aplikacji klasycznych platformy .NET** . W C++ przypadku baz kodu należy mieć zainstalowaną obsługę obciążeń dla **komputerów stacjonarnych C++**  .

### <a name="codebases-that-use-custom-build-tools"></a>Bazy kodu, które używają niestandardowych narzędzi kompilacji

Jeśli baza kodu używa niestandardowych narzędzi kompilacji, należy powiedzieć programowi Visual Studio, jak zbudować kod przy użyciu *zadań kompilacji* , które są zdefiniowane w pliku *JSON* . Aby uzyskać więcej informacji, zobacz [Dostosowywanie kompilacji i debugowania zadań](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

### <a name="codebases-that-contain-python-or-javascript-code"></a>Bazy kodu zawierające kod języka Python lub JavaScript

Jeśli baza kodu zawiera kod Python lub JavaScript, nie trzeba konfigurować żadnych plików *. JSON* , ale trzeba zainstalować odpowiednie obciążenie. Należy również skonfigurować skrypt uruchamiania:

1. Zainstaluj środowisko [programistyczne środowiska programowania Node. js](https://visualstudio.microsoft.com/vs/node-js/) lub programowania w języku [Python](https://visualstudio.microsoft.com/vs/python/) , wybierając **Narzędzia**  > **Pobierz narzędzia i funkcje**albo zamykając program Visual Studio i uruchamiając Instalator programu Visual Studio.

   ![Obciążenia dla środowiska Node. js i Python](media/python_nodejs_workloads.png)

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy lub menu kontekstowym pliku JavaScript lub Python, wybierz polecenie **Ustaw jako element startowy** .

1. Wybierz przycisk **Start** , aby rozpocząć debugowanie.

### <a name="codebases-that-contain-c-code"></a>Bazy kodu zawierające C++ kod

Aby uzyskać informacje na C++ temat otwierania kodu bez rozwiązań lub projektów w programie Visual Studio, zobacz [otwieranie C++folderu projects for ](/cpp/build/open-folder-projects-cpp).

### <a name="codebases-that-contain-a-visual-studio-project"></a>Bazy kodu zawierające projekt programu Visual Studio

Jeśli folder kodu zawiera projekt programu Visual Studio, można wyznaczyć projekt jako element startowy.

![Ustaw projekt jako element startowy](media/customize-set-project-as-startup-item.png)

Tekst przycisku **Start** zmieni się, aby odzwierciedlić, że projekt jest elementem startowym.

![Projekt przy przycisku Start](media/customize-start-button-project.png)

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie zadań kompilacji i debugowania](../ide/customize-build-and-debug-tasks-in-visual-studio.md)
- [Otwieranie folderu projektów na potrzeby języka C++](/cpp/build/open-folder-projects-cpp)
- [CMake projekty wC++](/cpp/build/cmake-projects-in-visual-studio)
- [Pisanie kodu w edytorze kodu i tekstu](../ide/writing-code-in-the-code-and-text-editor.md)