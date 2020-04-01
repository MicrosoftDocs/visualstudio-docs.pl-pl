---
title: 'Jak: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji | Dokumenty firmy Microsoft'
ms.date: 08/28/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84efda930066c4236fa4397fbadf287c6774fdb0
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472779"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Jak: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji

Po utworzeniu projektu w programie Visual Studio IDE, można wyświetlić informacje o tej kompilacji w oknie **dane wyjściowe.** Korzystając z tych informacji, można na przykład rozwiązać problem z awarią kompilacji.

- W przypadku projektów języka C++ można również wyświetlić te same informacje w pliku dziennika, który jest tworzony i zapisywany podczas tworzenia projektu. 

- W przypadku projektów kodu zarządzanego można kliknąć okno danych wyjściowych kompilacji i nacisnąć klawisz **Ctrl**+**S**. Program Visual Studio monituje o lokalizację, aby zapisać informacje z okna **dane wyjściowe** w pliku dziennika.

Ide można również użyć, aby określić, jakie rodzaje informacji, które mają być wyświetlane o każdej kompilacji.

Jeśli tworzysz dowolny rodzaj projektu przy użyciu MSBuild, można utworzyć plik dziennika, aby zapisać informacje o kompilacji. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-view-the-build-log-file-for-a-c-project"></a>Aby wyświetlić plik dziennika kompilacji dla projektu języka C++

1. W **Eksploratorze Windows** lub **Eksploratorze plików**otwórz następujący plik (względem folderu głównego projektu): *Zwolnij*\\<ProjectName>\>. Dziennik* lub *Debugowanie\\<\>ProjectName .log*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Aby utworzyć plik dziennika kompilacji dla projektu kodu zarządzanego

1. Na pasku menu wybierz pozycję **Build** > **Build Solution**.

2. W oknie **Dane wyjściowe** kliknij gdzieś w tekście.

3. Naciśnij **klawisze Ctrl**+**S**.

   Visual Studio monituje o lokalizację, aby zapisać dane wyjściowe kompilacji.

Dzienniki można również generować, uruchamiając msbuild bezpośrednio z `-fileLogger` `-fl`wiersza polecenia, używając opcji wiersza polecenia ( ) . Zobacz [Uzyskiwanie dzienników kompilacji za pomocą msbuild](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Aby zmienić ilość informacji zawartych w dzienniku kompilacji

1. Na pasku menu wybierz pozycję**Opcje** **narzędzi** > .

2. Na stronie **Projekty i rozwiązania** wybierz stronę **Kompilacja i uruchamianie.**

3. Na liście **pełnej szczegółowości kompilacji kompilacji projektu MSBuild** wybierz jedną z następujących wartości, a następnie wybierz przycisk **OK.**

    |Poziom szczegółowości|Opis|
    | - |-----------------|
    |**Ciche**|Wyświetla tylko podsumowanie kompilacji.|
    |**Minimalny**|Wyświetla podsumowanie kompilacji i błędy, ostrzeżenia i komunikaty, które są klasyfikowane jako bardzo ważne.|
    |**Normalne**|Wyświetla podsumowanie kompilacji; błędy, ostrzeżenia i komunikaty, które są klasyfikowane jako bardzo ważne; i główne etapy kompilacji. Ten poziom szczegółowości będzie najczęściej używany.|
    |**szczegółowo**|Wyświetla podsumowanie kompilacji; błędy, ostrzeżenia i komunikaty, które są klasyfikowane jako bardzo ważne; wszystkie kroki kompilacji; i wiadomości, które są klasyfikowane jako o normalnym znaczeniu.|
    |**Diagnostyczne**|Wyświetla wszystkie dane, które są dostępne dla kompilacji. Ten poziom szczegółowości służy do debugowania problemów z niestandardowymi skryptami kompilacji i innymi problemami z kompilacją.|

     Aby uzyskać więcej informacji, zobacz [Okno dialogowe Opcje, Projekty i rozwiązania, Tworzenie i uruchamianie](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) oraz <xref:Microsoft.Build.Framework.LoggerVerbosity>.

    > [!IMPORTANT]
    > Należy odbudować projekt dla zmian, aby zostały wprowadzone w oknie **Dane wyjściowe** (wszystkie projekty) i * \<ProjectName>.txt* pliku (tylko projekty C++).

## <a name="use-binary-logs-to-make-it-easier-to-browse-large-log-files"></a>Użyj dzienników binarnych, aby ułatwić przeglądanie dużych plików dziennika

Dzienniki binarne są opcjonalną funkcją dla projektów platformy .NET, która umożliwia bardziej bogatsze przeglądanie dzienników, które może ułatwić znajdowanie informacji w dużych dziennikach. Aby używać dzienników binarnych, zainstaluj [narzędzie Project System Tools](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools). Aby uzyskać więcej [https://msbuildlog.com](https://msbuildlog.com) informacji, zobacz dziennik [binarny i dziennik binarny](https://github.com/microsoft/msbuild/blob/master/documentation/wiki/Binary-Log.md)

## <a name="see-also"></a>Zobacz też

- [Twórz i twórz projekty i rozwiązania w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
