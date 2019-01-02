---
title: Tworzenie kodu bez projektów ani rozwiązań
ms.date: 02/21/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1275a5c0ada3ddc12fe4257880e16d130243d0e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968475"
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań

W programie Visual Studio 2017 można otworzyć kod z niemal dowolnego typu na podstawie katalogu projektu do programu Visual Studio bez konieczności plik rozwiązania lub projektu. Oznacza to, możesz można, na przykład klonowanie repozytorium w serwisie GitHub, otwórz go bezpośrednio w programie Visual Studio i rozpocząć tworzenie bez konieczności tworzenia rozwiązania lub projektu. Jeśli to konieczne, można określić zadania kompilacji niestandardowej i uruchom parametrów za pomocą prostego pliki w formacie JSON.

Po otwarciu plików kodu w programie Visual Studio, **Eksploratora rozwiązań** Wyświetla wszystkie pliki w folderze. Możesz kliknąć dowolny plik, aby rozpocząć jego edycji. W tle programu Visual Studio uruchamia indeksowanie plików, aby włączyć funkcję IntelliSense, nawigowanie i funkcje refaktoryzacji. Jak edytowanie, tworzenie, przenieść lub usunąć pliki programu Visual Studio automatycznie śledzi zmiany i stale aktualizuje jego indeksu funkcji IntelliSense. Za pomocą kolorowania składni i w wielu przypadkach, pojawi się kod obejmują podstawowe instrukcji IntelliSense.

## <a name="open-any-code"></a>Otwórz każdy kod

Kod można otworzyć w programie Visual Studio, w dowolnym z następujących sposobów:

- Na pasku menu programu Visual Studio, wybierz **pliku** > **Otwórz** > **folderu**, a następnie przejdź do lokalizacji kodu.
- Menu kontekstowe (kliknij prawym przyciskiem myszy) do folderu zawierającego kod, wybierz **Otwórz w programie Visual Studio** polecenia.
- Wybierz **Otwórz Folder** linku w programie Visual Studio **strona startowa**.
- Jeśli jesteś użytkownikiem klawiatury, naciśnij klawisz **Ctrl**+**Shift**+**Alt**+**O** w wizualizacji Studio.
- Otwórz kod ze sklonowanego repozytorium GitHub.

### <a name="to-open-code-from-a-cloned-github-repo"></a>Aby otworzyć kod ze sklonowanego repozytorium GitHub

Poniższy przykład pokazuje, jak klonowanie repozytorium GitHub, a następnie otwórz swój kod w programie Visual Studio. Aby wykonać tę procedurę, musisz mieć konto usługi GitHub i Git dla Windows instalowanych w systemie. Zobacz [utworzeniem nowego konta usługi GitHub](https://help.github.com/articles/signing-up-for-a-new-github-account/) i [Git dla Windows](https://git-for-windows.github.io/) Aby uzyskać więcej informacji.

1. Przejdź do repozytorium, które chcesz sklonować w witrynie GitHub.

1. Wybierz **Klonuj lub Pobierz** przycisk, a następnie wybierz **Kopiuj do Schowka** przycisk menu rozwijane, aby skopiować bezpieczny adres URL repozytorium usługi GitHub.

   ![GitHub przycisku klonowania](./media/VSIDE_Code_Clone.png)

1. W programie Visual Studio, wybierz **Team Explorer** kartę, aby otworzyć **Team Explorer**. Jeśli karta nie jest widoczna, otwórz go z **widoku** > **Team Explorer**.

1. W programie Team Explorer w obszarze **lokalne repozytoria Git** wybierz pozycję **klonowania** polecenia, a następnie wklej adres URL strony GitHub, w polu tekstowym.

   ![Klonowanie projektu](./media/VSIDE_Code_Clone2.png)

1. Wybierz **klonowania** przycisk, aby sklonować pliki projektu do lokalnego repozytorium Git. W zależności od rozmiaru repozytorium ten proces może potrwać kilka minut.

1. Po repozytorium zostało sklonowane w systemie, w w **Team Explorer**, wybierz **Otwórz** polecenia na menu kontekstowe (kliknij prawym przyciskiem myszy) nowo sklonowanego repozytorium.

   ![Sklonowane repozytorium](./media/VSIDE_Code_Clone3.png)

1. Wybierz **Pokaż widok folderu** polecenie, aby wyświetlić pliki w **Eksploratora rozwiązań**.

   ![Pokaż widok folderu](./media/VSIDE_Code_Clone3_show.png)

   Można teraz przeglądać foldery i pliki na sklonowane repozytorium i wyświetlić i wyszukiwanie kodu w edytorze kodu programu Visual Studio wraz z kolorowania składni i inne funkcje.

| | |
|---------|---------|
| ![Ikona aparatu filmu wideo](../install/media/video-icon.png)| [Obejrzyj film wideo](https://mva.microsoft.com/en-us/training-courses/getting-started-with-visual-studio-2017-17798?l=lp3TOKD6D_6711787171) na temat sposobu Klonuj i otwórz kod z repozytorium GitHub w programie Visual Studio. |

## <a name="run-and-debug-your-code"></a>Uruchamianie i debugowanie kodu

Można debugować kodu w programie Visual Studio bez projektów ani rozwiązań! Aby debugować w niektórych językach, konieczne może być Podaj prawidłową *plik startowy* w bazie kodu, takich jak skrypt, plik wykonywalny lub projektu. Pole listy rozwijanej obok **Start** przycisk na pasku narzędzi, zawiera listę wszystkich elementów uruchamiania, które program Visual Studio wykryje, a także elementy, które w szczególności wyznaczyć. Visual Studio uruchamia ten kod najpierw podczas debugowania kodu.

Konfigurowanie kodu do uruchamiania w programie Visual Studio różni się w zależności od tego, jakiego typu kod jest i co to są narzędzia do kompilacji.

### <a name="codebases-that-use-msbuild"></a>Bazach kodu, które używają programu MSBuild

Opartych na platformie MSBuild bazach kodu może mieć wielu konfiguracjach kompilacji, które pojawiają się w **Start** przycisku listy rozwijanej. Wybierz plik, który ma być używany jako element startowy, a następnie wybierz **Start** przycisk, aby rozpocząć debugowanie.

> [!NOTE]
> Aby uzyskać C# i bazach kodu języka Visual Basic, konieczne jest posiadanie **programowanie aplikacji klasycznych dla platformy .NET** zainstalowanym obciążeniem. Dla kodu C++, konieczne jest posiadanie **programowanie aplikacji klasycznych w języku C++** zainstalowanym obciążeniem.

### <a name="codebases-that-use-custom-build-tools"></a>Bazach kodu tego użycie niestandardowych narzędzi kompilacji

Jeśli Twoja używa kodu niestandardowego narzędzia kompilacji, a następnie musisz poinformować programu Visual Studio jak tworzyć zawartość przy użyciu kodu *zadania kompilacji* które są definiowane w *.json* pliku. Aby uzyskać więcej informacji, zobacz [Dostosowywanie kompilacji i debugowania zadań](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

### <a name="codebases-that-contain-python-or-javascript-code"></a>Bazach kodu, które zawierają kod JavaScript, Python

Jeśli baza kodu zawiera kod języka Python lub JavaScript, nie trzeba skonfigurować dowolne *.json* pliki, ale trzeba instalować odpowiedniej obciążenia. Należy także skonfigurować skrypt uruchamiania:

1. Zainstaluj [programowania Node.js](https://visualstudio.microsoft.com/vs/node-js/) lub [programowania w języku Python](https://visualstudio.microsoft.com/vs/python/) obciążenie, wybierając **narzędzia** > **Pobierz narzędzia i funkcje**, lub zamknięciu programu Visual Studio, a następnie uruchamiając Instalatora programu Visual Studio.

   ![Obciążeń deweloperskich środowiska node.js i Python](media/python_nodejs_workloads.png)

1. W **Eksploratora rozwiązań**, w menu kontekście lub kliknij prawym przyciskiem myszy plik JavaScript lub Python wybierz **Ustaw jako element startowy** polecenia.

1. Wybierz **Start** przycisk, aby rozpocząć debugowanie.

### <a name="codebases-that-contain-c-code"></a>Bazach kodu, który zawiera kod języka C++

Aby dowiedzieć się, jak otwieranie kodu C++ bez rozwiązań lub projektów w programie Visual Studio, zobacz [Otwórz Folder projektów w języku C++](/cpp/ide/non-msbuild-projects).

### <a name="codebases-that-contain-a-visual-studio-project"></a>Bazach kodu zawierające projekt programu Visual Studio

Jeśli folder kodu zawiera projekt programu Visual Studio, możesz wyznaczyć projektu jako element startowy.

![Zestaw projektu jako element startowy](media/customize-set-project-as-startup-item.png)

**Start** zmiany tekstu przycisku, aby odzwierciedlić, że projekt jest element startowy.

![Projekt na przycisk Start](media/customize-start-button-project.png)

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie zadań kompilacji i debugowania](../ide/customize-build-and-debug-tasks-in-visual-studio.md)
- [Otwórz Folder projektów w języku C++](/cpp/ide/non-msbuild-projects)
- [Projekty CMake w języku C++](/cpp/ide/cmake-tools-for-visual-cpp)
- [Pisanie kodu w edytorze tekstu i kodu](../ide/writing-code-in-the-code-and-text-editor.md)