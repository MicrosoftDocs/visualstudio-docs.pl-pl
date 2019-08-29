---
title: 'Instrukcje: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji | Microsoft Docs'
ms.date: 08/28/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1fe1932930c869e3d4d3d74eb641da068e1cffec
ms.sourcegitcommit: 3cda0d58c5cf1985122b8977b33a171c7359f324
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154811"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Instrukcje: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji

Po skompilowaniu projektu w środowisku IDE programu Visual Studio można wyświetlić informacje o tej kompilacji w oknie **danych wyjściowych** . Korzystając z tych informacji, można na przykład rozwiązać problem z niepowodzeniem kompilacji. 

- W C++ przypadku projektów można także wyświetlić te same informacje w pliku *txt* , który został utworzony i zapisany automatycznie. 

- W przypadku projektów kodu zarządzanego można kliknąć w oknie kompilacja wyjściowa i nacisnąć **klawisze CTRL**+**S**. Program Visual Studio poprosi o lokalizację, aby zapisać informacje z okna **danych wyjściowych** w pliku *txt* . 

Możesz również użyć IDE, aby określić, jakiego rodzaju informacje mają być wyświetlane dla każdej kompilacji.

W przypadku kompilowania dowolnego rodzaju projektu przy użyciu programu MSBuild można utworzyć plik *txt* , aby zapisać informacje o kompilacji. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-view-the-build-log-file-for-a-c-project"></a>Aby wyświetlić plik dziennika kompilacji dla C++ projektu

1. W **Eksploratorze Windows** lub **Eksploratorze plików**Otwórz następujący plik:  *\\. ..\Visual Studio \<w wersji\>\Projects\\<\\ProjectName <\> ProjectName\>\debug.\\<ProjectName\>. txt*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Aby utworzyć plik dziennika kompilacji dla projektu kodu zarządzanego

1. Na pasku menu wybierz polecenie **Kompiluj** > **kompilację rozwiązania**.

2. W oknie **dane wyjściowe** kliknij gdziekolwiek w tekście.

3. Naciśnij **klawisze CTRL**+**S**.

   Program Visual Studio poprosi o lokalizację, w której mają zostać zapisane dane wyjściowe kompilacji.

Dzienniki można również generować przez uruchomienie programu MSBuild bezpośrednio z wiersza polecenia przy użyciu `-fileLogger` opcji wiersza polecenia (`-fl`). Zobacz [Uzyskiwanie dzienników kompilacji za pomocą programu MSBuild](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Aby zmienić ilość informacji zawartych w dzienniku kompilacji

1. Na pasku menu wybierz **narzędzia** > **opcje**.

2. Na stronie **projekty i rozwiązania** wybierz stronę **kompilacja i uruchomienie** .

3. Na liście **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** wybierz jedną z następujących wartości, a następnie wybierz przycisk **OK** .

    |Poziom szczegółowości|Opis|
    | - |-----------------|
    |**Otoczeniu**|Wyświetla podsumowanie tylko kompilacji.|
    |**Mniejsze**|Wyświetla podsumowanie kompilacji i błędów, ostrzeżeń i komunikatów, które są skategoryzowane jako bardzo ważne.|
    |**Typow**|Wyświetla podsumowanie kompilacji; błędy, ostrzeżenia i komunikaty, które są klasyfikowane jako bardzo ważne; i główne kroki kompilacji. Ten poziom szczegółów będzie używany najczęściej.|
    |**Szczegółowości**|Wyświetla podsumowanie kompilacji; błędy, ostrzeżenia i komunikaty, które są klasyfikowane jako bardzo ważne; wszystkie kroki kompilacji; i wiadomości, które są podzielone na normalne znaczenie.|
    |**Diagnostyce**|Wyświetla wszystkie dane, które są dostępne dla kompilacji. Możesz użyć tego poziomu szczegółowości, aby pomóc w debugowaniu problemów z niestandardowymi skryptami kompilacji i innymi problemami z kompilacją.|

     Aby uzyskać więcej informacji, zobacz [okno dialogowe Opcje, projekty i rozwiązania, kompilacja i uruchomienie](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) oraz <xref:Microsoft.Build.Framework.LoggerVerbosity>.

    > [!IMPORTANT]
    > Musisz ponownie skompilować projekt, aby zmiany zaczęły obowiązywać w oknie **danych wyjściowych** (wszystkie projekty) iC++  *\<pliku ProjectName >. txt* (tylko projekty).

## <a name="use-binary-logs-to-make-it-easier-to-browse-large-log-files"></a>Używanie dzienników binarnych w celu łatwiejszego przeglądania dużych plików dziennika

Dzienniki binarne to opcjonalna funkcja projektów platformy .NET, która umożliwia bogatsze środowisko przeglądania dzienników, które może ułatwić znalezienie informacji w dużych dziennikach. Aby użyć dzienników binarnych, zainstaluj [narzędzia systemu projektu](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools). Aby uzyskać więcej informacji, [https://msbuildlog.com](https://msbuildlog.com) Zobacz i [dziennik binarny](https://github.com/microsoft/msbuild/blob/master/documentation/wiki/Binary-Log.md)

## <a name="see-also"></a>Zobacz także

- [Twórz i czyść projekty i rozwiązania w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
