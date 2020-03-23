---
title: Kompilacja budynku
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b5f00b3e71f0deb15d6266640db39751f2ae22f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76269100"
---
# <a name="compile-and-build-in-visual-studio"></a>Kompilowanie i tworzenie w programie Visual Studio

Aby uzyskać pierwsze wprowadzenie do tworzenia w ramach IDE, zobacz [Instruktaż: Tworzenie aplikacji](walkthrough-building-an-application.md).

Do utworzenia aplikacji można użyć dowolnej z następujących metod: ide programu Visual Studio, narzędzia wiersza polecenia MSBuild i potoki platformy Azure:

| Metoda kompilacji | Korzyści |
| --- |--- | --- |
| IDE |- Tworzenie kompilacji natychmiast i przetestować je w debugera.<br />- Uruchamianie kompilacji wieloprocesorowych dla projektów W języku C++ i C#.<br />- Dostosuj różne aspekty systemu kompilacji. |
| CMake | - Tworzenie projektów za pomocą narzędzia CMake<br />- Użyj tego samego systemu kompilacji na platformach Linux i Windows. |
| Wiersz polecenia MSBuild| - Tworzenie projektów bez instalowania programu Visual Studio.<br />- Uruchamianie kompilacji wieloprocesorowych dla wszystkich typów projektów.<br />- Dostosuj większość obszarów systemu kompilacji.|
| Azure Pipelines | - Automatyzacja procesu kompilacji w ramach ciągłej integracji / ciągłego dostarczania rurociągu.<br />- Zastosuj zautomatyzowane testy z każdym kompilacji.<br />- Zatrudniaj praktycznie nieograniczone zasoby oparte na chmurze do tworzenia procesów.<br />- Zmodyfikuj przepływ pracy kompilacji i tworzenie działań kompilacji do wykonywania zadań głęboko dostosowane.|

Dokumentacja w tej sekcji przechodzi do dalszych szczegółów procesu kompilacji opartej na IDE. Aby uzyskać więcej informacji na temat innych metod, zobacz [MSBuild](../msbuild/msbuild.md) i [Azure Potoki](/azure/devops/pipelines/index?view=vsts), odpowiednio.

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. W przypadku programu Visual Studio dla komputerów Mac zobacz [Kompilowanie i tworzenie w programie Visual Studio dla komputerów Mac](/visualstudio/mac/compiling-and-building).

## <a name="overview-of-building-from-the-ide"></a>Przegląd budynku z IDE

Podczas tworzenia projektu visual studio utworzone domyślne konfiguracje kompilacji dla projektu i rozwiązania, które zawiera projekt.  Te konfiguracje definiują sposób zarządzania i wdrażania rozwiązań i projektów. Konfiguracje projektu w szczególności są unikatowe dla platformy docelowej (takich jak Windows lub Linux) i typ kompilacji (takich jak debugowanie lub wydanie). Można edytować te konfiguracje, jak chcesz, a także można utworzyć własne konfiguracje w razie potrzeby.

Aby uzyskać pierwsze wprowadzenie do tworzenia w ramach IDE, zobacz [Instruktaż: Tworzenie aplikacji](walkthrough-building-an-application.md).

Następnie zobacz [Tworzenie i czyszczenie projektów i rozwiązań w programie Visual Studio,](building-and-cleaning-projects-and-solutions-in-visual-studio.md) aby dowiedzieć się więcej o różnych aspektach dostosowań, które można wprowadzić w procesie. Dostosowania obejmują [zmianę katalogów wyjściowych,](how-to-change-the-build-output-directory.md) [określanie niestandardowych zdarzeń kompilacji,](specifying-custom-build-events-in-visual-studio.md) [zarządzanie zależnościami projektu,](how-to-create-and-remove-project-dependencies.md) [zarządzanie plikami dziennika kompilacji](how-to-view-save-and-configure-build-log-files.md)i [pomijanie ostrzeżeń kompilatora.](how-to-suppress-compiler-warnings.md)

Stamtąd można zbadać wiele innych zadań:
- [Opis konfiguracji kompilacji](understanding-build-configurations.md)
- [Opis platform kompilacji](understanding-build-platforms.md)
- [Zarządzanie właściwościami projektu i rozwiązania](managing-project-and-solution-properties.md).
- Określ zdarzenia kompilacji w [językach C#](how-to-specify-build-events-csharp.md) i [Visual Basic](how-to-specify-build-events-visual-basic.md).
- [Ustawianie opcji kompilacji](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Twórz wiele projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="see-also"></a>Zobacz też

- [Budowanie (kompilowanie) projektów stron internetowych](https://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)
- [Kompilowanie i tworzenie (Visual Studio dla komputerów Mac)](/visualstudio/mac/compiling-and-building)
- [CZło projektów w programie Visual Studio](/cpp/build/cmake-projects-in-visual-studio)
