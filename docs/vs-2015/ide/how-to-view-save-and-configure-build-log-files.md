---
title: 'Instrukcje: wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffc1c620136c55c42f3468129ed164075d762bff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670505"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Poradnik: Oglądanie, zapisywanie i konfigurowanie plików dziennika kompilacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po skompilowaniu projektu w środowisku IDE programu Visual Studio można wyświetlić informacje o tej kompilacji w oknie **danych wyjściowych** . Korzystając z tych informacji, można na przykład rozwiązać problem z niepowodzeniem kompilacji. W C++ przypadku projektów można także wyświetlić te same informacje w pliku txt, który został utworzony i zapisany automatycznie. W przypadku projektów kodu zarządzanego można kopiować i wklejać informacje z okna **dane wyjściowe** do pliku. txt i zapisywać je samodzielnie. Możesz również użyć IDE, aby określić, jakiego rodzaju informacje mają być wyświetlane dla każdej kompilacji.

 W przypadku kompilowania dowolnego rodzaju projektu przy użyciu programu MSBuild można utworzyć plik txt, aby zapisać informacje o kompilacji. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).

### <a name="to-view-the-build-log-file-for-a-c-project"></a>Aby wyświetlić plik dziennika kompilacji dla C++ projektu

1. W **Eksploratorze Windows** lub **Eksploratorze plików**otwórz następujący plik: \\. ..\Visual Studio w *wersji*\Projects \\*ProjectName* \\*ProjectName*\debug. \\*ProjectName*. txt

### <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Aby utworzyć plik dziennika kompilacji dla projektu kodu zarządzanego

1. Na pasku menu wybierz **kompilacja**, **Kompiluj rozwiązanie**.

2. W oknie **dane wyjściowe** zaznacz informacje z kompilacji, a następnie skopiuj je do Schowka.

3. Otwórz Edytor tekstu, taki jak Notatnik, wklej informacje do pliku, a następnie zapisz go.

### <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Aby zmienić ilość informacji zawartych w dzienniku kompilacji

1. Na pasku menu wybierz **Narzędzia**, **Opcje**.

2. Na stronie **projekty i rozwiązania** wybierz stronę **kompilacja i uruchomienie** .

3. Na liście **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** wybierz jedną z następujących wartości, a następnie wybierz przycisk **OK** .

    |Poziom szczegółowości|Opis|
    |---------------------|-----------------|
    |Quiet|Wyświetla podsumowanie tylko kompilacji.|
    |Mniejsze|Wyświetla podsumowanie kompilacji i błędów, ostrzeżeń i komunikatów, które są skategoryzowane jako bardzo ważne.|
    |Typow|Wyświetla podsumowanie kompilacji; błędy, ostrzeżenia i komunikaty, które są klasyfikowane jako bardzo ważne; i główne kroki kompilacji. Ten poziom szczegółów będzie używany najczęściej.|
    |Szczegółowości|Wyświetla podsumowanie kompilacji; błędy, ostrzeżenia i komunikaty, które są klasyfikowane jako bardzo ważne; wszystkie kroki kompilacji; i wiadomości, które są podzielone na normalne znaczenie.|
    |Diagnostyce|Wyświetla wszystkie dane, które są dostępne dla kompilacji. Możesz użyć tego poziomu szczegółowości, aby pomóc w debugowaniu problemów z niestandardowymi skryptami kompilacji i innymi problemami z kompilacją.|

     Aby uzyskać więcej informacji, zobacz [okno dialogowe Opcje, projekty i rozwiązania, kompilacja i uruchomienie](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) oraz <xref:Microsoft.Build.Framework.LoggerVerbosity>.

    > [!IMPORTANT]
    > Musisz ponownie skompilować projekt, aby zmiany zaczęły obowiązywać w oknie **danych wyjściowych** (wszystkie projekty) i pliku *ProjectName*. txt (C++ tylko projekty).

## <a name="see-also"></a>Zobacz też
 [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md) [kompilowania i czyszczenia projektów oraz rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [kompilowania i kompilowania](../ide/compiling-and-building-in-visual-studio.md)
