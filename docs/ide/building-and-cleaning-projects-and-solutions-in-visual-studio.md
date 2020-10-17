---
title: Kompilowanie oraz oczyszczanie projektów i rozwiązań
description: Dowiedz się, jak tworzyć, odbudować lub czyścić wszystkie lub niektóre projekty lub elementy projektu w rozwiązaniu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d2ab8a723b69f4c5930c91a10719a2107ad83003
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136800"
---
# <a name="build-and-clean-projects-and-solutions-in-visual-studio"></a>Twórz i czyść projekty i rozwiązania w programie Visual Studio

Korzystając z procedur opisanych w tym temacie, można tworzyć, odbudować lub czyścić wszystkie lub niektóre projekty lub elementy projektu w rozwiązaniu. Aby zapoznać się z samouczkiem krok po kroku, zobacz [Przewodnik: kompilowanie aplikacji](../ide/walkthrough-building-an-application.md).

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Tworzenie i czyszczenie projektów oraz rozwiązań w programie Visual Studio dla komputerów Mac](/visualstudio/mac/building-and-cleaning-projects-and-solutions).

> [!NOTE]
> Interfejs użytkownika w wydaniu programu Visual Studio może się różnić od tego, co opisano w tym temacie, w zależności od aktywnych ustawień. Aby zmienić ustawienia, na przykład **Ogólne** lub **Visual C++** ustawienia, wybierz pozycję **Narzędzia**  >  **Importuj i Eksportuj ustawienia**, a następnie wybierz pozycję **Zresetuj wszystkie ustawienia**.

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Aby skompilować, skompilować lub wyczyścić całe rozwiązanie

1. W **Eksplorator rozwiązań**wybierz lub Otwórz rozwiązanie.

2. Na pasku menu wybierz **kompilacja**, a następnie wybierz jedno z następujących poleceń:

    - Wybierz **Kompiluj** lub **Kompiluj rozwiązanie** , aby skompilować tylko te pliki projektu i składniki, które uległy zmianie od czasu ostatniej kompilacji.

        > [!NOTE]
        > Polecenie **Build** zostaje **skompilowane rozwiązanie** , gdy rozwiązanie zawiera więcej niż jeden projekt.

    - Wybierz opcję **Kompiluj ponownie rozwiązanie** , aby usunąć rozwiązanie, a następnie Skompiluj wszystkie pliki i składniki projektu.

    - Wybierz pozycję **Wyczyść rozwiązanie** , aby usunąć wszystkie pliki pośrednie i wyjściowe. Tylko w przypadku pozostałych plików projektu i składników można skompilować nowe wystąpienia plików pośrednich i wyjściowych.

## <a name="to-build-or-rebuild-a-single-project"></a>Aby skompilować lub skompilować pojedynczy projekt

1. W **Eksplorator rozwiązań**wybierz lub Otwórz projekt.

2. Na pasku menu wybierz **kompilacja**, a następnie wybierz opcję **Kompiluj** *ProjectName* lub **Skompiluj ponownie** *ProjectName*.

    - Wybierz pozycję **Kompiluj** *ProjectName* , aby skompilować tylko składniki projektu, które uległy zmianie od czasu ostatniej kompilacji.

    - Wybierz pozycję **Kompiluj ponownie** *ProjectName* , aby usunąć "czysty" projekt, a następnie Skompiluj pliki projektu i wszystkie składniki projektu.

## <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Aby skompilować tylko projekt startowy i jego zależności

1. Na pasku menu wybierz **Narzędzia**  >  **Opcje**.

2. W oknie dialogowym **Opcje** rozwiń węzeł **projekty i rozwiązania** , a następnie wybierz stronę **kompilacja i uruchomienie** .

     Zostanie otwarte okno dialogowe Opcje **kompilowania i uruchamiania**  >  **projektów i rozwiązań**  >  **Options** .

3. Zaznacz pole wyboru  **Kompiluj tylko projekty startowe i zależności przy uruchamianiu** .

     Gdy to pole wyboru jest zaznaczone, tylko bieżący projekt startowy i jego zależności są kompilowane podczas wykonywania jednego z następujących kroków:

    - Na pasku menu wybierz **Debuguj**  >  **Start** (**F5**).

    - Na pasku menu wybierz kolejno opcje **Kompiluj**kompilacje  >  **rozwiązanie** (**Ctrl** + **SHIFT** + **B**).

    Gdy to pole wyboru jest wyczyszczone, wszystkie projekty, ich zależności i pliki rozwiązań są kompilowane po uruchomieniu jednego z powyższych poleceń. To pole wyboru jest domyślnie wyczyszczone.

## <a name="to-build-only-the-selected-visual-c-project"></a>Aby skompilować tylko wybrany projekt Visual C++

Wybierz [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projekt, a następnie na pasku menu wybierz kolejno opcje **Kompiluj**  >  **projekt**i jedno z następujących poleceń:

- **Tylko kompilacja** *ProjectName*

- **Kompiluj tylko** *ProjectName*

- **Wyczyść tylko** *ProjectName*

- **Tylko link** *ProjectName*

Te polecenia mają zastosowanie tylko do [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] wybranego projektu, bez kompilowania, ponownego kompilowania, czyszczenia lub łączenia jakichkolwiek zależności projektu lub plików rozwiązania. W zależności od używanej wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , podmenu **tylko projekt** może zawierać więcej poleceń.

## <a name="to-compile-multiple-c-project-items"></a>Aby skompilować wiele elementów projektu C++

W **Eksplorator rozwiązań**wybierz wiele plików, które mogą być skompilowanymi akcjami, otwórz menu skrótów dla jednego z tych plików, a następnie wybierz polecenie **Kompiluj**.

Jeśli pliki mają zależności, pliki zostaną skompilowane w kolejności zależności. Operacja kompilowania zakończy się niepowodzeniem, jeśli pliki wymagają prekompilowanego nagłówka, który nie jest dostępny podczas kompilowania. Operacja Kompiluj używa bieżącej aktywnej konfiguracji rozwiązania.

## <a name="to-stop-a-build"></a>Aby zatrzymać kompilację

Wykonaj jedną z następujących czynności:

- Na pasku menu wybierz opcję **Kompiluj**  >  **Anuluj**.

- Naciśnij klawisz **Ctrl** + **Break**.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji](../ide/how-to-view-save-and-configure-build-log-files.md)
- [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Kompilowanie i kompilowanie](../ide/compiling-and-building-in-visual-studio.md)
- [Ogólne informacje o konfiguracjach kompilacji](../ide/understanding-build-configurations.md)
- [Instrukcje: ustawienia konfiguracji Debug i Release](../debugger/how-to-set-debug-and-release-configurations.md)
- [Dokumentacja konstrukcyjna języka C/C++](/cpp/build/reference/c-cpp-building-reference)
- [Przełączniki wiersza polecenia devenv](../ide/reference/devenv-command-line-switches.md)
- [Rozwiązania i projekty](../ide/solutions-and-projects-in-visual-studio.md)
- [Twórz i oczyść projekty i rozwiązania (Visual Studio dla komputerów Mac)](/visualstudio/mac/building-and-cleaning-projects-and-solutions)
