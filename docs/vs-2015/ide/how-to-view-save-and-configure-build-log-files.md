---
title: 'Instrukcje: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7bd8bae0213755b11c145c4bef9c312fe3990c4d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432331"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Instrukcje: Wyświetlanie, zapisywanie i konfigurowanie plików dziennika kompilacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Po skompilowaniu projektu w środowisku IDE programu Visual Studio można wyświetlić informacje o tej kompilacji w **dane wyjściowe** okna. Za pomocą tych informacji, można na przykład rozwiązywania problemów dotyczących niepowodzenia kompilacji. Dla projektów języka C++ możesz wyświetlić te same informacje w pliku txt, który został utworzony i zapisywane automatycznie. Dla projektów kodu zarządzanego, można skopiować i wkleić informacje z **dane wyjściowe** okna do .txt plik i zapisz go samodzielnie. Aby określić, jakiego rodzaju informacje mają być wyświetlane dotyczące każdej kompilacji umożliwia także środowiska IDE.  
  
 Jeśli tworzysz dowolny rodzaj projektu przy użyciu programu MSBuild, można utworzyć pliku txt, aby zapisać informacje o kompilacji. Aby uzyskać więcej informacji, zobacz [uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
### <a name="to-view-the-build-log-file-for-a-c-project"></a>Aby wyświetlić plik dziennika kompilacji dla projektu w języku C++  
  
1. W **Eksplorator Windows** lub **Eksploratora plików**, otwórz następujący plik: \\...\Visual Studio *wersji*\Projects\\  *ProjectName*\\*ProjectName*\Debug\\*ProjectName*txt  
  
### <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Aby utworzyć plik dziennika kompilacji dla projektu kodu zarządzanego  
  
1. Na pasku menu wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
2. W **dane wyjściowe** , wyróżnić informacje z kompilacji, a następnie skopiuj do Schowka.  
  
3. Otwórz Edytor tekstów, takiego jak Notatnik, wklej je do pliku, a następnie zapisz go.  
  
### <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Aby zmienić ilość informacji zawartych w dzienniku kompilacji  
  
1. Na pasku menu wybierz **narzędzia**, **opcje**.  
  
2. Na **projekty i rozwiązania** wybierz **kompilowanie i uruchamianie** strony.  
  
3. W **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** , wybierz jedną z następujących wartości, a następnie wybierz **OK** przycisku.  
  
    |Poziom szczegółowości|Opis|  
    |---------------------|-----------------|  
    |Quiet|Wyświetla podsumowanie kompilacji tylko.|  
    |Minimalny|Wyświetla podsumowanie kompilacji i błędy, ostrzeżenia i komunikaty, które są podzielone jako bardzo ważne.|  
    |Normalne|Wyświetla podsumowanie kompilacji; błędy, ostrzeżenia i komunikaty, które są klasyfikowane jako bardzo ważne; i główne kroki kompilacji. Taki poziom szczegółowości będzie najczęściej używany.|  
    |Szczegółowe|Wyświetla podsumowanie kompilacji; błędy, ostrzeżenia i komunikaty, które są klasyfikowane jako bardzo ważne; wszystkie kroki kompilacji; i komunikatów, które są podzielone od normalnych znaczenie.|  
    |Diagnostyka|Wyświetla wszystkie dane, które jest dostępne dla kompilacji. Taki poziom szczegółowości można użyć do debugowania problemów ze skryptami niestandardowej kompilacji i inne problemy z kompilacją.|  
  
     Aby uzyskać więcej informacji, zobacz [okno dialogowe Opcje, projekty i rozwiązania, kompilacji i uruchomienia](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) i <xref:Microsoft.Build.Framework.LoggerVerbosity>.  
  
    > [!IMPORTANT]
    > Należy przebudować projekt, aby zmiany zaczęły obowiązywać **dane wyjściowe** okna (wszystkie projekty) i *ProjectName*pliku txt (tylko dla projektów C++).  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Kompilowanie oraz Oczyszczanie projektów i rozwiązań w programie Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Kompilowanie i tworzenie](../ide/compiling-and-building-in-visual-studio.md)
