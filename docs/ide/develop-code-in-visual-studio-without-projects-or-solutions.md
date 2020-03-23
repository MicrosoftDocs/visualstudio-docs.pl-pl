---
title: Tworzenie kodu bez projektów ani rozwiązań
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- open folder [Visual Studio]
- anycode [Visual Studio]
- projects and solutions, develop code without
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7a9459868d569a7466dccf92e4b548c0500bf80
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596297"
---
# <a name="develop-code-in-visual-studio-without-projects-or-solutions"></a>Tworzenie kodu w programie Visual Studio bez projektów ani rozwiązań

Można otworzyć kod z prawie każdego typu projektu opartego na katalogu do programu Visual Studio bez konieczności rozwiązania lub pliku projektu. Oznacza to, że można na przykład sklonować repozytorium w usłudze GitHub, otworzyć je bezpośrednio w programie Visual Studio i rozpocząć tworzenie bez konieczności tworzenia rozwiązania lub projektu. W razie potrzeby można określić niestandardowe zadania kompilacji i uruchomić parametry za pomocą prostych plików JSON.

Po otwarciu plików kodu w programie Visual Studio **Eksplorator rozwiązań** wyświetla wszystkie pliki w folderze. Możesz kliknąć dowolny plik, aby rozpocząć jego edycję. W tle visual studio rozpoczyna indeksowanie plików, aby włączyć IntelliSense, nawigacji i refaktoryzacji funkcji. Podczas edytowania, tworzenia, przenoszenia lub usuwania plików program Visual Studio śledzi zmiany automatycznie i stale aktualizuje swój indeks IntelliSense. Kod pojawi się z kolorowania składni i, w wielu przypadkach, zawierać podstawowe IntelliSense zakończenia instrukcji.

## <a name="open-any-code"></a>Otwórz dowolny kod

Kod można otworzyć w programie Visual Studio w dowolny z następujących sposobów:

- Na pasku menu programu Visual Studio wybierz pozycję **Folder** > **otwierania** > **pliku,** a następnie przejdź do lokalizacji kodu.

- W menu kontekstu (kliknięcie prawym przyciskiem myszy) folderu zawierającego kod wybierz polecenie **Otwórz w programie Visual Studio.**

::: moniker range="vs-2017"
- Wybierz **łącze Otwórz folder** na **stronie startowej**programu Visual Studio .
::: moniker-end

::: moniker range=">=vs-2019"
- Wybierz łącze **Otwórz folder** w oknie startowym.
::: moniker-end

- Jeśli jesteś użytkownikiem klawiatury, naciśnij **klawisze Ctrl**+**Shift**+**Alt**+**O** w programie Visual Studio.

- Otwórz kod ze sklonowanego repozytorium GitHub.

### <a name="to-open-code-from-a-cloned-github-repo"></a>Aby otworzyć kod ze sklonowanego repozytorium GitHub

W poniższym przykładzie pokazano, jak sklonować repozytorium GitHub, a następnie otworzyć jego kod w programie Visual Studio. Aby wykonać tę procedurę, musisz mieć konto GitHub i git dla systemu Windows zainstalowany w systemie. Aby uzyskać więcej informacji, zobacz [Rejestrowanie nowego konta Usługi GitHub](https://help.github.com/articles/signing-up-for-a-new-github-account/) i [git dla systemu Windows.](https://git-for-windows.github.io/)

1. Przejdź do repozytorium, które chcesz sklonować w usłudze GitHub.

1. Wybierz przycisk **Klonuj lub Pobierz,** a następnie wybierz przycisk **Kopiuj do Schowka** w menu rozwijanym, aby skopiować bezpieczny adres URL repozytorium GitHub.

   ![Przycisk klonowania GitHub](./media/VSIDE_Code_Clone.png)

1. W programie Visual Studio wybierz kartę **Eksplorator zespołu,** aby otworzyć **Eksploratora zespołu**. Jeśli nie widzisz karty, otwórz ją w programie **View** > **Team Explorer**.

1. W Eksploratorze zespołu w sekcji **Lokalne repozytoria Git** wybierz polecenie **Klonuj,** a następnie wklej adres URL strony GitHub w polu tekstowym.

   ![Klonowanie projektu](./media/VSIDE_Code_Clone2.png)

1. Wybierz przycisk **Klonuj,** aby sklonować pliki projektu do lokalnego repozytorium Git. W zależności od rozmiaru repozytorium ten proces może potrwać kilka minut.

1. Po sklonowanie repozytorium do systemu w **Eksploratorze zespołu**wybierz polecenie **Otwórz** w menu kontekstu (kliknij prawym przyciskiem myszy) nowo sklonowanego repozytorium.

   ![Sklonowane repo](./media/VSIDE_Code_Clone3.png)

1. Wybierz polecenie **Pokaż widok folderu,** aby wyświetlić pliki w **Eksploratorze rozwiązań**.

   ![Pokaż widok folderu](./media/VSIDE_Code_Clone3_show.png)

   Teraz można przeglądać foldery i pliki w sklonowanym repozytorium oraz wyświetlać i przeszukiwać kod w edytorze kodu programu Visual Studio wraz z kolorowaniem składni i innymi funkcjami.

## <a name="run-and-debug-your-code"></a>Uruchamianie i debugowanie kodu

Można debugować kod w programie Visual Studio bez projektu lub rozwiązania! Aby debugować niektóre języki, może być konieczne określenie prawidłowego *pliku startowego* w bazie kodu, takiego jak skrypt, plik wykonywalny lub projekt. Pole listy rozwijanej obok przycisku **Start** na pasku narzędzi zawiera listę wszystkich elementów startowych wykrytych przez program Visual Studio, a także elementów, które zostały specjalnie wyznaczone. Visual Studio uruchamia ten kod po pierwszym debugowaniu kodu.

Konfigurowanie kodu do uruchamiania w programie Visual Studio różni się w zależności od rodzaju kodu jest i jakie są narzędzia kompilacji.

### <a name="codebases-that-use-msbuild"></a>Bazy kodu korzystające z usługi MSBuild

Bazy kodu oparte na msbuild mogą mieć wiele konfiguracji kompilacji, które pojawiają się na liście rozwijanej przycisku **Start.** Wybierz plik, którego chcesz użyć jako elementu startowego, a następnie wybierz przycisk **Start,** aby rozpocząć debugowanie.

> [!NOTE]
> W przypadku baz kodu języka C# i Visual Basic musi być zainstalowane obciążenie **programistyczne dla komputerów .NET.** W przypadku baz kodu języka C++ musi być zainstalowany program rozwoju pulpitu z zainstalowanym obciążeniem **języka C++.**

### <a name="codebases-that-use-custom-build-tools"></a>Bazy kodu korzystające z niestandardowych narzędzi kompilacji

Jeśli baza kodu używa niestandardowych narzędzi kompilacji, należy poinformować program Visual Studio, jak utworzyć kod przy użyciu *zadań kompilacji,* które są zdefiniowane w pliku *.json.* Aby uzyskać więcej informacji, zobacz [Dostosowywanie zadań kompilacji i debugowania](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

### <a name="codebases-that-contain-python-or-javascript-code"></a>Bazy kodu zawierające kod Języka Python lub JavaScript

Jeśli baza kodu zawiera kod Języka Python lub JavaScript, nie trzeba konfigurować żadnych plików *.json,* ale musisz zainstalować odpowiednie obciążenie. Należy również skonfigurować skrypt startowy:

1. Zainstaluj [deweloperskie node.js](https://visualstudio.microsoft.com/vs/node-js/) lub obciążenie [deweloperskie języka Python,](https://visualstudio.microsoft.com/vs/python/) wybierając **polecenie Narzędzia** > **Pobierz narzędzia i funkcje**lub zamykając program Visual Studio i uruchamiając Instalatora programu Visual Studio.

   ![Obciążenia deweloperów node.js i Python](media/python_nodejs_workloads.png)

1. W **Eksploratorze rozwiązań**w menu prawym przyciskiem myszy lub w menu kontekstowym pliku JavaScript lub Python wybierz polecenie **Ustaw jako element startowy.**

1. Wybierz przycisk **Start,** aby rozpocząć debugowanie.

### <a name="codebases-that-contain-c-code"></a>Bazy kodu zawierające kod języka C++

Aby uzyskać informacje na temat otwierania kodu języka C++ bez rozwiązań lub projektów w programie Visual Studio, zobacz [Otwieranie projektów folderów dla języka C++](/cpp/build/open-folder-projects-cpp).

### <a name="codebases-that-contain-a-visual-studio-project"></a>Bazy kodu zawierające projekt programu Visual Studio

Jeśli folder kodu zawiera projekt programu Visual Studio, można wyznaczyć projekt jako element startowy.

![Ustawianie projektu jako elementu startowego](media/customize-set-project-as-startup-item.png)

Tekst przycisku **Start** zmienia się, aby odzwierciedlić, że projekt jest elementem startowym.

![Przycisk Projektuj na starcie](media/customize-start-button-project.png)

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie zadań kompilacji i debugowania](../ide/customize-build-and-debug-tasks-in-visual-studio.md)
- [Otwieranie folderu projektów na potrzeby języka C++](/cpp/build/open-folder-projects-cpp)
- [CZło projektów w języku C++](/cpp/build/cmake-projects-in-visual-studio)
- [Pisanie kodu w edytorze kodu i tekstu](../ide/writing-code-in-the-code-and-text-editor.md)
