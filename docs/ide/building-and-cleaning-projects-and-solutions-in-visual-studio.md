---
title: Kompilowanie oraz Oczyszczanie projektów i rozwiązań
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
f1_keywords:
- VS.BuildProjectPicker
- vs.batchbuild
helpviewer_keywords:
- Clean Solution command
- builds [Visual Studio], managing
- solution build configurations, starting
- Build Solution command
- project build configurations, starting
- build configurations, starting
- project build configurations, dependencies
- Rebuild Solution command
- solution build configurations, build order
- builds [Visual Studio], preparing
ms.assetid: 710891fd-379e-42c2-a84b-44a7af694ca0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25d9f278ab63ddfa4ffbbf72a4899ce99828b720
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942756"
---
# <a name="build-and-clean-projects-and-solutions-in-visual-studio"></a>Kompilowanie i czyszczenie projektów i rozwiązań w programie Visual Studio

Korzystając z procedur opisanych w tym temacie, można utworzyć, odbudować lub wyczyścić wszystkie lub niektóre projekty lub elementy projektu w rozwiązaniu. Aby uzyskać samouczek krok po kroku, zobacz [instruktażu: Tworzenie aplikacji](../ide/walkthrough-building-an-application.md).

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [— kompilowanie i czyszczenie projektów i rozwiązań w programie Visual Studio dla komputerów Mac](/visualstudio/mac/building-and-cleaning-projects-and-solutions).

> [!NOTE]
> Interfejs użytkownika w Twojej wersji programu Visual Studio mogą różnić się od co w tym temacie opisano, w zależności od aktywnych ustawień. Aby zmienić swoje ustawienia, na przykład aby **ogólne** lub **Visual C++** ustawienia, wybierz **narzędzia** > **Import i eksport ustawień**, a następnie wybierz **Resetuj wszystkie ustawienia**.

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Do kompilacji, odbudować lub Wyczyść całe rozwiązanie

1.  W **Eksploratora rozwiązań**, wybierz lub Otwórz rozwiązanie.

2.  Na pasku menu wybierz **kompilacji**, a następnie wybierz jedno z następujących poleceń:

    -   Wybierz **kompilacji** lub **Kompiluj rozwiązanie** skompilować tylko tych projektów, plików i składników, które zmieniły się od najnowszej kompilacji.

        > [!NOTE]
        > **Kompilacji** staje się polecenia **Kompiluj rozwiązanie** gdy rozwiązanie zawiera więcej niż jeden projekt.

    -   Wybierz **Kompiluj rozwiązanie** do rozwiązania "Wyczyść", a następnie skompilowanie wszystkich plików projektu i składników.

    -   Wybierz **czyste rozwiązanie** można usunąć wszystkich plików pośrednich i wynikowych. Za pomocą tylko projektu, jak i składnika pliki po lewej nowe wystąpienia pośrednich i pliki wyjściowe może następnie być skompilowana.

## <a name="to-build-or-rebuild-a-single-project"></a>Aby skompilować lub ponownie skompilować pojedynczego projektu

1.  W **Eksploratora rozwiązań**, wybrać lub otworzyć projektu.

2.  Na pasku menu wybierz **kompilacji**, a następnie wybierz **kompilacji** *ProjectName* lub **odbudować** *ProjectName*.

    -   Wybierz **kompilacji** *ProjectName* tworzenie tylko tych projektów składników, które zmieniły się od najnowszej kompilacji.

    -   Wybierz **odbudować** *ProjectName* do projektu "Wyczyść", a następnie skompiluj pliki projektu i wszystkich składników projektów.

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Aby skompilować tylko projekt startowy i jego zależności

1.  Na pasku menu wybierz **narzędzia** > **opcje**.

2.  W **opcje** okna dialogowego rozwiń **projekty i rozwiązania** węzła, a następnie wybierz **kompilowanie i uruchamianie** strony.

     **Kompilowanie i uruchamianie** > **projekty i rozwiązania** > **opcje** zostanie otwarte okno dialogowe.

3.  Wybierz **tylko tworzyć projekty startowe i zależności przy uruchomieniu** pole wyboru.

     Gdy to pole wyboru jest zaznaczone, tylko bieżący projekt startowy i jego zależności są tworzone podczas wykonywania jednej z następujących czynności:

    -   Na pasku menu wybierz **debugowania** > **Start** (**F5**).

    -   Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie** (**Ctrl**+**Shift** +  **B**).

    Gdy to pole wyboru jest wyczyszczone, wszystkie projekty, ich zależności i pliki rozwiązania są tworzone po uruchomieniu dowolnego z powyższych poleceń. Domyślnie to pole wyboru jest wyczyszczone.

## <a name="to-build-only-the-selected-visual-c-project"></a>Można tworzyć tylko dla wybranego projektu Visual C++

Wybierz [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektu, a następnie na pasku menu wybierz **kompilacji** > **projektu tylko**i jeden z następujących poleceń:

- **Tylko kompilacja** *ProjectName*

- **Ponownie skompiluj tylko** *ProjectName*

- **Czyszczenie tylko** *ProjectName*

- **Połącz tylko** *ProjectName*

Polecenia te dotyczą tylko programu [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektu, która została wybrana, bez tworzenia, ponownie skompilować, czyszczenia i łączenie wszystkie zależności projektu lub rozwiązania pliki. W zależności od używanej wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], **projektu tylko** podmenu może zawierać więcej poleceń.

## <a name="to-compile-multiple-c-project-items"></a>Aby skompilować wiele elementów projektu C++

W **Eksploratora rozwiązań**, wybierz wiele plików, które mają może być skompilowany akcji, otwórz menu skrótów dla jednego z tych plików, a następnie wybierz **skompilować**.

Jeśli pliki mają zależności, pliki zostanie skompilowany w kolejności wg zależności. Operacja kompilacji zakończy się niepowodzeniem, jeśli pliki wymagają prekompilowanego nagłówka, który nie jest dostępny podczas kompilacji. Operacja kompilacji używa bieżącej aktywnej konfiguracji rozwiązania.

## <a name="to-stop-a-build"></a>Aby zatrzymać kompilację

Wykonaj jedną z następujących czynności:

- Na pasku menu wybierz **kompilacji** > **anulować**.

- Naciśnij klawisz **Ctrl**+**Przerwij**.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Kompilowanie i tworzenie](../ide/compiling-and-building-in-visual-studio.md)
- [Ogólne informacje o konfiguracjach kompilacji](../ide/understanding-build-configurations.md)
- [Instrukcje: Zestaw debugowania i zwalniania konfiguracji](../debugger/how-to-set-debug-and-release-configurations.md)
- [Odwołanie kompilacji C/C++](/cpp/build/reference/c-cpp-building-reference)
- [Przełączniki wiersza polecenia Devenv](../ide/reference/devenv-command-line-switches.md)
- [Rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Kompilowanie i czyszczenie projektów i rozwiązań (Visual Studio dla komputerów Mac)](/visualstudio/mac/building-and-cleaning-projects-and-solutions)