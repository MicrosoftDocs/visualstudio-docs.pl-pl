---
title: Tworzenie pakietów rozwiązania SharePoint | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f7afee863d36796bb481f9aca2c24a9ba891ae7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952729"
---
# <a name="create-sharepoint-solution-packages"></a>Tworzenie pakietów rozwiązania SharePoint
  Przy użyciu projektanta pakietów, można tworzyć i dostosowywać pakiety wdrożeniowe. Na przykład można dodać elementów projektu programu SharePoint i funkcji, resetowanie na serwerze usług IIS, ustaw zakresy aktywacji funkcji i zidentyfikować zależności funkcji. Projektant generuje również manifest pliku XML, który zawiera opis każdego pakietu.

## <a name="packaging-tools"></a>Narzędzia do tworzenia pakietów
 Możesz użyć **projektancie pakietu** dostosować pakietu i wygenerować manifest. Może zawierać elementów projektu programu SharePoint, skonfigurować serwer sieci Web należy zresetować i skonfigurować typ serwera wdrożenia. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

 Alternatywnie, można użyć **Eksploratora pakietów** Aby zmodyfikować funkcje i elementy w pliku pakietu (*.wsp*). Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu Eksploratora pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

 Można użyć programu Visual Studio i MSBuild, aby utworzyć pakiet (*.wsp*) pliki do wdrożenia rozwiązania programu SharePoint. Ten proces generuje pliki manifestu potrzebne do wdrożenia programu SharePoint. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).

## <a name="package-designer-options"></a>Opcje projektanta pakietów
 W poniższej tabeli przedstawiono właściwości, które można dostosować do pakietów programu SharePoint przy użyciu **projektancie pakietu**.

|Właściwość projektanta pakietu|Opis ustawienia domyślne|
|-------------------------------|------------------------------------|
|Nazwa|Wymagana. Domyślna nazwa pakietu jest równa *ProjectName*.|
|Resetuj serwer sieci Web|Opcjonalna. Wybierz, jeśli chcesz ponownie uruchomić serwer sieci Web po *.wsp* plik jest instalowany na serwerze programu SharePoint.|
|Typ serwera wdrożenia|Wymagana. Domyślnie ustawiono zakres ApplicationServer.<br /><br /> ApplicationServer: W tym artykule opisano serwera, który jest hostem usług.<br /><br /> WebFrontEnd: W tym artykule opisano serwera, który jest hostem witryny sieci Web.|
|Elementów w rozwiązaniu|Wszystkie elementy projektu programu SharePoint i funkcje, które można dodać do pakietu.|
|Elementy w pakiecie|Opcjonalna. Wszystkie elementy programu SharePoint i funkcje, które mają zostać wdrożone w pakiecie.|

## <a name="configure-the-packaging-process"></a>Skonfiguruj proces tworzenia pakietu
 Po opracowywania rozwiązań programu SharePoint w programie Visual Studio, można dostosować, jak są pakowane projektów.

 W poniższej tabeli przedstawiono dwa obiekty docelowe programu MSBuild, które można dostosować sposób, w jaki *.wsp* zostanie utworzony plik.

|Cel|Opis|
|------------|-----------------|
|BeforeLayout|Obiekt docelowy, który wykonuje zadania od razu, zanim pliki są kopiowane do katalogu, pośrednich. Pliki można zmodyfikować przed utworzeniem pliku pakietu (*.wsp*).|
|AfterLayout|Obiekt docelowy, który wykonuje zadania natychmiast po zakończeniu pliki są kopiowane do katalogu, pośrednich.|

 Aby uzyskać więcej informacji [jak: Dostosowywanie pakietu rozwiązania SharePoint przy użyciu docelowych elementów MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).

## <a name="packaging-architecture"></a>Architektura pakietu
 Wykonane następujące kroki podczas tworzenia pakietu programu SharePoint (*.wsp*) w programie Visual Studio.

1. Funkcji i pakietów są weryfikowane, aby upewnić się, że struktury fizyczne i semantyczne pakietu jest poprawna.

2. Funkcje, elementy projektów i plików pakietu w pakiecie są wyliczane. Pliki manifestu pakietów i funkcje są przekształcane obejmujący wszystkie niezbędne informacje dotyczące wdrażania i aktywacji. Tokeny są zastępowane pełną wartość.

3. Można dostosować element docelowy programu BeforeLayout MSBuild jest wykonywane. Możesz utworzyć ten krok, aby wprowadzać żadnych zmian niestandardowy pakiet przed *.wsp* zostanie utworzony plik.

4. Wyliczany pliki są kopiowane do katalogu, pośrednich.

5. Można dostosować element docelowy programu MSBuild AfterLayout jest wykonywane. Możesz utworzyć ten krok, aby wprowadzać żadnych zmian niestandardowy pakiet przed *.wsp* zostanie utworzony plik.

6. Pliki w katalogu pośrednim zostaną dodane do *.wsp* pliku.

## <a name="package-folder-structure"></a>Struktura folderów pakietu
 Podczas pakowania projektu programu SharePoint *.wsp* plik zostanie utworzony w *SolutionFolder\bin\\\<BuildConfiguration >* folderu. Na przykład, jeśli Twoje rozwiązanie jest w *2013\Projects\ListDefinition1 C:\Visual Studio* i konfiguracji kompilacji jest ustawiona na wersji *.wsp* plik znajduje się w *2013\ C:\Visual Studio Projects\ListDefinition1\bin\Release*.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Instrukcje: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
- [Instrukcje: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Instrukcje: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Instrukcje: Dostosowywanie pakietu rozwiązania SharePoint przy użyciu docelowych elementów MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)
