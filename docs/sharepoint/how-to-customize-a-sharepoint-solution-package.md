---
title: 'Instrukcje: Dostosowywanie pakietu rozwiązania programu SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5e1c2e86f489191c3876154143706be4f9b0f1e4
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874942"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Instrukcje: Dostosowywanie pakietu rozwiązania SharePoint
  W Projektancie pakietu można użyć do tworzenia i dostosowywania pakietu (*.wsp*). Na przykład można dodać elementów projektu programu SharePoint i funkcje, określić, czy serwer sieci Web jest zresetować po wdrożeniu rozwiązania i Ustaw typ serwera wdrożenia.  
  
## <a name="open-the-package-designer"></a>Otwórz projektanta pakietów  
  
#### <a name="to-open-the-package-designer"></a>Aby otworzyć projektanta pakietów
  
-   W **Eksploratora rozwiązań**, kliknij dwukrotnie **pakietu**, lub wybierz **Projektant widoków** menu skrótów dla **pakietu**.  
  
## <a name="view-the-packaged-manifestffile"></a>Wyświetl spakowanych manifestfFile  
 W Projektancie pakietu można użyć do zmodyfikowania, a następnie wygenerować pakowanego pliku manifestu. Następnie można wyświetlić kod XML dla tego pliku w programie Visual Studio.  
  
#### <a name="to-view-the-xml-source-file"></a>Aby wyświetlić plik źródłowy XML  
  
1.  W **projektancie pakietu**, wybierz **manifestu**.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Aby wyświetlić spakowany plik manifestu za pomocą Eksploratora rozwiązań  
  
1.  W **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki**.  
  
2.  Rozwiń węzeł pakietu, rozwiń Package.package, a następnie otwórz *Package.Template.xml* pliku.  
  
    > [!NOTE]  
    >  Po otwarciu pliku manifestu XML dla szablonu pakietu, pliki są automatycznie zweryfikowana, i można zignorować te ostrzeżenia, które pojawiają się w oknie Lista błędów.  
  
## <a name="change-the-manifest-template"></a>Zmiana szablonu manifestu  
 Możesz zmienić kod XML dla pakowanego pliku manifestu w edytorze XML programu Visual Studio lub w okienku manifestu szablonu. Wszelkie zmiany w kodzie XML są scalane w pakowanego pliku manifestu pakietu.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Aby zmienić szablon manifestu za pomocą edytora XML  
  
1.  W **projektancie pakietu**, wybierz **manifestu** kartę, a następnie rozwiń **opcje edytowania** węzła, a następnie wybierz **otwarty w edytorze XML** łącze.  
  
     Zmiany w pliku XML są scalane w spakowanym pliku manifestu.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Aby zmienić szablon manifestu przy użyciu okienka szablonu manifestu  
  
1.  W **projektancie pakietu**, wybierz **manifestu** kartę, a następnie rozwiń **opcje edytowania** węzeł, a następnie zmień plik XML, który jest wyświetlany w okienku manifestu szablonu.  
  
     Zmiany w pliku XML są wyświetlane w okienku **Podgląd spakowanego manifestu**.  
  
## <a name="overwrite-the-packaged-manifest-file"></a>Zastąpienie spakowanego pliku manifestu  
 Można wyłączyć projektanta pakietów i utworzyć *manifest.xml* plik ręcznie. Aby wykonać tę procedurę, po raz pierwszy bieżące ustawienia w Projektancie pakietu są zapisywane w pliku XML pakietu szablonu. Następnie można zmodyfikować lub zastąpić ten kod XML.  
  
> [!NOTE]  
>  Jeśli dodawanie lub usuwanie elementów projektu programu SharePoint i funkcji w pliku XML, gdy projektant pakietu jest wyłączony, nie są spakowane te elementy projektu i funkcje.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Aby zastąpić spakowany plik manifestu poprzez wyłączenie projektanta  
  
1.  W **projektancie pakietu**, wybierz **manifestu** kartę.  
  
2.  Rozwiń węzeł **Opcje edycji**, wybierz link **Zastąp wygenerowany kod XML i edytuj manifest w edytorze XML**, a następnie wybierz przycisk **Tak**.  
  
     Szablon zostanie zaktualizowany o spakowany plik bieżącego manifestu.  
  
## <a name="enable-the-package-designer"></a>Włącz projektanta pakietów  
 Można ponownie włączyć projektanta pakietów, aby dostosować *manifest.xml* pliku.  
  
#### <a name="to-re-enable-the-designer"></a>Aby ponownie włączyć Projektanta  
  
1.  W **projektancie pakietu**, wybierz **Odrzuć modyfikacje manifestu i ponownie włącz projektanta** łącze, a następnie wybierz **tak** przycisku.  
  
     Szablon zostanie odświeżony z początkowym tekstem, a zmiany wprowadzone w pliku XML zostaną utracone.  
  
## <a name="see-also"></a>Zobacz także
 [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
