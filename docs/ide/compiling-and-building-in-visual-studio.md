---
title: Kompilowanie budynku
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
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269100"
---
# <a name="compile-and-build-in-visual-studio"></a>Kompilowanie i kompilowanie w programie Visual Studio

Pierwsze wprowadzenie do kompilowania w środowisku IDE zawiera [Przewodnik: kompilowanie aplikacji](walkthrough-building-an-application.md).

Możesz użyć dowolnej z następujących metod, aby skompilować aplikację: środowisko IDE programu Visual Studio, narzędzia wiersza polecenia programu MSBuild i Azure Pipelines:

| Metoda kompilacji | Zalety |
| --- |--- | --- |
| IDE |— Natychmiast Twórz kompilacje i Testuj je w debugerze.<br />— Uruchom kompilacje wieloprocesorowe C++ dla C# projektów i.<br />-Dostosowywanie różnych aspektów systemu kompilacji. |
| CMake | -Kompiluj projekty przy użyciu narzędzia CMake<br />— Użyj tego samego systemu kompilacji na platformach Linux i Windows. |
| Wiersz polecenia MSBuild| -Kompiluj projekty bez instalowania programu Visual Studio.<br />— Uruchom kompilacje wieloprocesorowe dla wszystkich typów projektów.<br />-Dostosowywanie większości obszarów systemu kompilacji.|
| Azure Pipelines | — Automatyzuj proces kompilacji w ramach potoku ciągłej integracji/ciągłego dostarczania.<br />-Zastosuj testy automatyczne przy każdej kompilacji.<br />— Wykorzystuj praktycznie nieograniczone zasoby oparte na chmurze dla procesów kompilacji.<br />— Modyfikuj przepływ pracy kompilacji i twórz działania kompilacji, aby wykonywać głęboko dostosowane zadania.|

Dokumentacja w tej sekcji zawiera dalsze szczegóły procesu kompilacji opartego na środowisku IDE. Aby uzyskać więcej informacji o innych metodach, zobacz odpowiednio [MSBuild](../msbuild/msbuild.md) i [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Kompilowanie i kompilowanie w Visual Studio dla komputerów Mac](/visualstudio/mac/compiling-and-building).

## <a name="overview-of-building-from-the-ide"></a>Przegląd kompilowania z poziomu środowiska IDE

Podczas tworzenia projektu program Visual Studio utworzył domyślne konfiguracje kompilacji dla projektu i rozwiązania, które zawiera projekt.  Te konfiguracje definiują sposób kompilowania i wdrażania rozwiązań i projektów. Konfiguracje projektu w szczególności są unikatowe dla platformy docelowej (na przykład Windows lub Linux) i typu kompilacji (na przykład debugowanie lub wydanie). Te konfiguracje można edytować w dowolny sposób, a także w razie konieczności tworzyć własne konfiguracje.

Pierwsze wprowadzenie do kompilowania w środowisku IDE zawiera [Przewodnik: kompilowanie aplikacji](walkthrough-building-an-application.md).

Następnie zapoznaj się z [tworzeniem i czyszczeniem projektów i rozwiązań w programie Visual Studio](building-and-cleaning-projects-and-solutions-in-visual-studio.md) , aby dowiedzieć się więcej o różnych aspektach dostosowań, które można wykonać w procesie. Dostosowania obejmują [zmianę katalogów wyjściowych](how-to-change-the-build-output-directory.md), [Określanie niestandardowych zdarzeń kompilacji](specifying-custom-build-events-in-visual-studio.md), [Zarządzanie zależnościami projektu](how-to-create-and-remove-project-dependencies.md), [Zarządzanie plikami dzienników kompilacji](how-to-view-save-and-configure-build-log-files.md)i [pomijanie ostrzeżeń kompilatora](how-to-suppress-compiler-warnings.md).

Z tego miejsca możesz poznać różne inne zadania:
- [Informacje o konfiguracjach kompilacji](understanding-build-configurations.md)
- [Informacje o platformach kompilacji](understanding-build-platforms.md)
- [Zarządzaj właściwościami projektu i rozwiązania](managing-project-and-solution-properties.md).
- Określ zdarzenia kompilacji w [C#](how-to-specify-build-events-csharp.md) i [Visual Basic](how-to-specify-build-events-visual-basic.md).
- [Ustawianie opcji kompilacji](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Równoległe kompilowanie wielu projektów](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).

## <a name="see-also"></a>Zobacz także

- [Kompilowanie (Kompilowanie) projektów witryny sieci Web](https://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)
- [Kompiluj i Kompiluj (Visual Studio dla komputerów Mac)](/visualstudio/mac/compiling-and-building)
- [CMake projekty w programie Visual Studio](/cpp/build/cmake-projects-in-visual-studio)
