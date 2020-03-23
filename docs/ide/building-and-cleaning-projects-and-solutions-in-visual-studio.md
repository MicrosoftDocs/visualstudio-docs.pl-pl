---
title: Kompilowanie oraz oczyszczanie projektów i rozwiązań
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1cf71abb19f6d4a3a459b4e5559e536f18f41c8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114560"
---
# <a name="build-and-clean-projects-and-solutions-in-visual-studio"></a>Twórz i twórz projekty i rozwiązania w programie Visual Studio

Za pomocą procedur w tym temacie, można skompilować, odbudować lub wyczyścić wszystkie lub niektóre projekty lub elementy projektu w rozwiązaniu. Aby zapoznać się z samouczkiem krok po kroku, zobacz [Instruktaż: Tworzenie aplikacji](../ide/walkthrough-building-an-application.md).

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. W programie Visual Studio dla komputerów Mac zobacz [Tworzenie i czyszczenie projektów i rozwiązań w programie Visual Studio dla komputerów Mac.](/visualstudio/mac/building-and-cleaning-projects-and-solutions)

> [!NOTE]
> Interfejs użytkownika w wersji programu Visual Studio może się różnić od tego, co opisano w tym temacie, w zależności od aktywnych ustawień. Aby zmienić ustawienia, na przykład na **Ustawienia ogólne** lub **Visual C++,** wybierz pozycję Ustawienia**importu i eksportu** **narzędzi,** > a następnie wybierz pozycję **Resetuj wszystkie ustawienia**.

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Aby zbudować, odbudować lub wyczyścić całe rozwiązanie

1. W **Eksploratorze rozwiązań**wybierz lub otwórz rozwiązanie.

2. Na pasku menu wybierz pozycję **Buduj**, a następnie wybierz jedno z następujących poleceń:

    - Wybierz **opcję Kompilacja** lub **rozwiązanie kompilacji,** aby skompilować tylko te pliki projektu i składniki, które uległy zmianie od czasu ostatniej kompilacji.

        > [!NOTE]
        > Polecenie **Kompilacja** staje się **rozwiązaniem kompilacji,** gdy rozwiązanie zawiera więcej niż jeden projekt.

    - Wybierz **opcję Odbuduj rozwiązanie,** aby "wyczyścić" rozwiązanie, a następnie skompilować wszystkie pliki i składniki projektu.

    - Wybierz **pozycję Clean Solution,** aby usunąć wszystkie pliki pośrednie i wyjściowe. Po lewej stronie pozostało tylko pliki projektu i składnika, można następnie zbudować nowe wystąpienia plików pośrednich i wyjściowych.

## <a name="to-build-or-rebuild-a-single-project"></a>Aby zbudować lub odbudować pojedynczy projekt

1. W **Eksploratorze rozwiązań**wybierz lub otwórz projekt.

2. Na pasku menu wybierz polecenie **Buduj**, a następnie wybierz pozycję **Buduj** *projectname* lub **Odbuduj** *projectname*.

    - Wybierz **pozycję Build** *ProjectName,* aby utworzyć tylko te składniki projektu, które uległy zmianie od czasu ostatniej kompilacji.

    - Wybierz **pozycję Odbuduj** *ProjectName,* aby "wyczyścić" projekt, a następnie skompilować pliki projektu i wszystkie składniki projektu.

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Aby utworzyć tylko projekt startowy i jego zależności

1. Na pasku menu wybierz pozycję**Opcje** **narzędzi** > .

2. W oknie dialogowym **Opcje** rozwiń węzeł **Projekty i rozwiązania,** a następnie wybierz stronę **Kompilacja i uruchom.**

     Zostanie otwarte okno dialogowe **Tworzenie i uruchamianie** > projektów i opcji**rozwiązań.** > **Options**

3. Zaznacz pole wyboru **Tylko tworzenie projektów startowych i zależności w obszarze Uruchom.**

     Gdy to pole wyboru jest zaznaczone, tylko bieżący projekt startowy i jego zależności są tworzone podczas wykonywania jednego z następujących kroków:

    - Na pasku menu wybierz pozycję **Debug** > **Start** (**F5**).

    - Na pasku menu wybierz pozycję **Build** > **Build Solution** **(Ctrl**+**Shift**+**B**).

    Gdy to pole wyboru jest wyczyszczone, wszystkie projekty, ich zależności i pliki rozwiązania są tworzone po uruchomieniu jednego z powyższych poleceń. To pole wyboru jest domyślnie wyczyszczone.

## <a name="to-build-only-the-selected-visual-c-project"></a>Aby utworzyć tylko wybrany projekt visual c++

Wybierz [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projekt, a następnie na pasku menu wybierz pozycję **Zbuduj** > **tylko projekt**i jedno z następujących poleceń:

- **Zbuduj tylko** *projectname*

- **Odbuduj tylko** *projectname*

- **Nazwa** *projektu* tylko do czyszczenia

- **Nazwa** *tylko łącza projectname*

Te polecenia dotyczą tylko [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] wybranego projektu, bez tworzenia, przebudowywania, czyszczenia lub łączenia zależności projektu lub plików rozwiązań. W zależności od [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]wersji podmenu **Tylko projekt** może zawierać więcej poleceń.

## <a name="to-compile-multiple-c-project-items"></a>Aby skompilować wiele elementów projektu języka C++

W **Eksploratorze rozwiązań**wybierz wiele plików, które mogą być kompilowane akcje, otwórz menu skrótów dla jednego z tych plików, a następnie wybierz polecenie **Skompiluj**.

Jeśli pliki mają zależności, pliki zostaną skompilowane w kolejności zależności. Operacja kompilacji zakończy się niepowodzeniem, jeśli pliki wymagają wstępnie skompilowanego nagłówka, który nie jest dostępny podczas kompilowania. Operacja kompilacji używa bieżącej konfiguracji aktywnego rozwiązania.

## <a name="to-stop-a-build"></a>Aby zatrzymać kompilację

Wykonaj jedną z następujących czynności:

- Na pasku menu wybierz pozycję **Zmiecie** > **anuluj**.

- Naciśnij **klawisze Ctrl**+**Break**.

## <a name="see-also"></a>Zobacz też

- [Jak: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Kompilacja i budowa](../ide/compiling-and-building-in-visual-studio.md)
- [Opis konfiguracji kompilacji](../ide/understanding-build-configurations.md)
- [Instrukcje: ustawienia konfiguracji Debug i Release](../debugger/how-to-set-debug-and-release-configurations.md)
- [C/C++ odniesienie do budynku](/cpp/build/reference/c-cpp-building-reference)
- [Przełączniki linii poleceń Devenv](../ide/reference/devenv-command-line-switches.md)
- [Rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Tworzenie i czyszczenie projektów i rozwiązań (Visual Studio dla komputerów Mac)](/visualstudio/mac/building-and-cleaning-projects-and-solutions)
