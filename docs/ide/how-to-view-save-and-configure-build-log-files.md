---
title: 'Instrukcje: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji | Microsoft Docs'
ms.date: 08/28/2019
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4acf8ca4e116bfb0ab990f1b0aed66bef95820ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283908"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Instrukcje: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji

Po skompilowaniu projektu w środowisku IDE programu Visual Studio można wyświetlić informacje o tej kompilacji w oknie **danych wyjściowych** . Korzystając z tych informacji, można na przykład rozwiązać problem z niepowodzeniem kompilacji.

- W przypadku projektów C++ można także wyświetlić te same informacje w pliku dziennika, który jest tworzony i zapisywany podczas kompilowania projektu. 

- W przypadku projektów kodu zarządzanego można kliknąć w oknie kompilacja wyjściowa i nacisnąć **klawisze CTRL** + **S**. Program Visual Studio poprosi o lokalizację, w której mają zostać zapisane informacje z okna **dane wyjściowe** do pliku dziennika.

Możesz również użyć IDE, aby określić, jakiego rodzaju informacje mają być wyświetlane dla każdej kompilacji.

W przypadku kompilowania dowolnego rodzaju projektu przy użyciu programu MSBuild można utworzyć plik dziennika, aby zapisać informacje o kompilacji. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-view-the-build-log-file-for-a-c-project"></a>Aby wyświetlić plik dziennika kompilacji dla projektu języka C++

1. W **Eksploratorze Windows** lub **Eksploratorze plików**Otwórz następujący plik (względem folderu głównego projektu): *Release* \\ <ProjectName> \> . Log * lub *Debug \\<ProjectName \> . log*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Aby utworzyć plik dziennika kompilacji dla projektu kodu zarządzanego

1. Na pasku menu wybierz polecenie **Kompiluj**  >  **kompilację rozwiązania**.

2. W oknie **dane wyjściowe** kliknij gdziekolwiek w tekście.

3. Naciśnij **klawisze CTRL** + **S**.

   Program Visual Studio poprosi o lokalizację, w której mają zostać zapisane dane wyjściowe kompilacji.

Dzienniki można również generować przez uruchomienie programu MSBuild bezpośrednio z wiersza polecenia przy użyciu `-fileLogger` `-fl` opcji wiersza polecenia (). Zobacz [Uzyskiwanie dzienników kompilacji za pomocą programu MSBuild](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Aby zmienić ilość informacji zawartych w dzienniku kompilacji

1. Na pasku menu wybierz **Narzędzia**  >  **Opcje**.

2. Na stronie **projekty i rozwiązania** wybierz stronę **kompilacja i uruchomienie** .

3. Na liście **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** wybierz jedną z następujących wartości, a następnie wybierz przycisk **OK** .

    |Poziom szczegółowości|Opis|
    | - |-----------------|
    |**Otoczeniu**|Wyświetla podsumowanie tylko kompilacji.|
    |**Minimalny**|Wyświetla podsumowanie kompilacji i błędów, ostrzeżeń i komunikatów, które są skategoryzowane jako bardzo ważne.|
    |**Typow**|Wyświetla podsumowanie kompilacji; błędy, ostrzeżenia i komunikaty, które są klasyfikowane jako bardzo ważne; i główne kroki kompilacji. Ten poziom szczegółów będzie używany najczęściej.|
    |**szczegółowo**|Wyświetla podsumowanie kompilacji; błędy, ostrzeżenia i komunikaty, które są klasyfikowane jako bardzo ważne; wszystkie kroki kompilacji; i wiadomości, które są podzielone na normalne znaczenie.|
    |**Diagnostyka**|Wyświetla wszystkie dane, które są dostępne dla kompilacji. Możesz użyć tego poziomu szczegółowości, aby pomóc w debugowaniu problemów z niestandardowymi skryptami kompilacji i innymi problemami z kompilacją.|

     Aby uzyskać więcej informacji, zobacz [okno dialogowe Opcje, projekty i rozwiązania, kompilacja i uruchomienie](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) oraz <xref:Microsoft.Build.Framework.LoggerVerbosity> .

    > [!IMPORTANT]
    > Musisz ponownie skompilować projekt, aby zmiany zaczęły obowiązywać w oknie **danych wyjściowych** (wszystkie projekty) i pliku * \<ProjectName> txt* (tylko projekty C++).

## <a name="use-binary-logs-to-make-it-easier-to-browse-large-log-files"></a>Używanie dzienników binarnych w celu łatwiejszego przeglądania dużych plików dziennika

Dzienniki binarne to opcjonalna funkcja projektów platformy .NET, która umożliwia bogatsze środowisko przeglądania dzienników, które może ułatwić znalezienie informacji w dużych dziennikach. Aby użyć dzienników binarnych, zainstaluj [narzędzia systemu projektu](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools). Aby uzyskać więcej informacji, zobacz [https://msbuildlog.com](https://msbuildlog.com) i [dziennik binarny](https://github.com/microsoft/msbuild/blob/master/documentation/wiki/Binary-Log.md)

## <a name="see-also"></a>Zobacz też

- [Twórz i czyść projekty i rozwiązania w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
