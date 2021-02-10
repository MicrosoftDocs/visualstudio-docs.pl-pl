---
title: Tworzenie pakietów rozwiązania SharePoint | Microsoft Docs
description: Tworzenie i dostosowywanie pakietów wdrożeniowych dla rozwiązań programu SharePoint za pomocą projektanta pakietów. Poznaj narzędzia pakietu, opcje projektanta i strukturę folderów.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 423fcaf54d1d46ddf92352f4ff8bdbb637bbe514
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949093"
---
# <a name="create-sharepoint-solution-packages"></a>Tworzenie pakietów rozwiązania SharePoint
  Za pomocą projektanta pakietów można tworzyć i dostosowywać pakiety wdrożeniowe. Można na przykład dodać elementy i funkcje projektu programu SharePoint, zresetować serwer usług IIS, ustawić zakresy aktywacji funkcji i zidentyfikować zależności funkcji. Projektant generuje również manifest, plik XML, który opisuje każdy pakiet.

## <a name="packaging-tools"></a>Narzędzia pakietu
 Możesz użyć **projektanta pakietów** , aby dostosować pakiet i wygenerować manifest. Możesz dołączyć elementy projektu programu SharePoint, określić, czy serwer sieci Web ma być resetowany, i ustawić typ serwera wdrażania. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

 Alternatywnie możesz użyć **Eksploratora pakietów** do zmodyfikowania funkcji i elementów w pliku pakietu (*. wsp*). Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu Eksploratora pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

 Możesz użyć programu Visual Studio i MSBuild do tworzenia plików pakietu (*wsp*), aby wdrożyć rozwiązanie SharePoint. Ten proces generuje pliki manifestu, które są zbędne do wdrożenia programu SharePoint. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).

## <a name="package-designer-options"></a>Opcje projektanta pakietów
 W poniższej tabeli przedstawiono właściwości, które można dostosować w pakietach programu SharePoint za pomocą **projektanta pakietów**.

|Właściwość projektanta pakietów|Opis ustawienia domyślnego|
|-------------------------------|------------------------------------|
|Nazwa|Wymagane. Domyślna nazwa pakietu jest ustawiona na *ProjectName*.|
|Zresetuj serwer WebServer|Opcjonalny. Wybierz, czy chcesz ponownie uruchomić serwer sieci Web po zainstalowaniu pliku *. wsp* na serwerze programu SharePoint.|
|Typ serwera wdrażania|Opcjonalny. Reprezentuje typ serwera, który hostuje pakiet. Jeśli ta wartość nie zostanie ustawiona, wartość domyślna to webfronton.<br /><br /> ApplicationServer: opisuje serwer, który hostuje usługi.<br /><br /> Webfronton: opisuje serwer, który hostuje witryny sieci Web.|
|Elementy w rozwiązaniu|Wszystkie elementy projektu programu SharePoint i funkcje, które można dodać do pakietu.|
|Elementy w pakiecie|Opcjonalny. Wszystkie elementy i funkcje programu SharePoint, które mają zostać wdrożone w pakiecie.|

## <a name="configure-the-packaging-process"></a>Konfigurowanie procesu tworzenia pakietów
 Po opracowaniu rozwiązań programu SharePoint w programie Visual Studio można dostosować sposób pakowania projektów.

 W poniższej tabeli przedstawiono dwa elementy docelowe programu MSBuild, których można użyć do dostosowania sposobu tworzenia pliku *. wsp* .

|Cel|Opis|
|------------|-----------------|
|BeforeLayout|Obiekt docelowy, który wykonuje zadania bezpośrednio przed plikami, jest kopiowany do katalogu pośredniego. Pliki można modyfikować przed utworzeniem pliku pakietu (*wsp*).|
|AfterLayout|Obiekt docelowy, który wykonuje zadania bezpośrednio po plikach, jest kopiowany do katalogu pośredniego.|

 Aby uzyskać więcej informacji, [jak: Dostosowywanie pakietu rozwiązania SharePoint przy użyciu elementów docelowych programu MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).

## <a name="packaging-architecture"></a>Architektura pakietów
 Poniższe kroki są wykonywane podczas tworzenia pakietu programu SharePoint (*. wsp*) w programie Visual Studio.

1. Funkcje i pakiety są sprawdzane w celu upewnienia się, że struktura fizyczna i semantyczna pakietu jest poprawna.

2. Funkcje, elementy projektu i pliki pakietów w pakiecie są wyliczane. Pliki manifestu dla pakietów i funkcji są przekształcane w celu uwzględnienia wszystkich niezbędnych informacji na potrzeby wdrożenia i aktywacji. Tokeny są zastępowane w pełni kwalifikowaną wartością.

3. Zostanie wykonany dostosowywalny obiekt docelowy programu MSBuild BeforeLayout. Ten krok można utworzyć, aby wprowadzić wszelkie niestandardowe modyfikacje pakietu przed utworzeniem pliku *. wsp* .

4. Pliki wyliczane są kopiowane do katalogu pośredniego.

5. Zostanie wykonany dostosowywalny obiekt docelowy programu MSBuild AfterLayout. Ten krok można utworzyć, aby wprowadzić wszelkie niestandardowe modyfikacje pakietu przed utworzeniem pliku *. wsp* .

6. Pliki w katalogu pośrednim są dodawane do pliku *wsp* .

## <a name="package-folder-structure"></a>Struktura folderu pakietu
 Podczas pakowania projektu programu SharePoint plik *. wsp* jest tworzony w folderze *SolutionFolder\bin \\ \<BuildConfiguration>* . Na przykład jeśli Twoje rozwiązanie jest w *C:\Visual Studio 2013 \ Projects\ListDefinition1* i konfiguracja kompilacji jest ustawiona na wartość Release, plik *. wsp* znajduje się w *C:\Visual Studio 2013 \ Projects\ListDefinition1\bin\Release*.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Instrukcje: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu projektanta pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
- [Instrukcje: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Instrukcje: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Instrukcje: Dostosowywanie pakietu rozwiązania SharePoint przy użyciu elementów docelowych MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)
