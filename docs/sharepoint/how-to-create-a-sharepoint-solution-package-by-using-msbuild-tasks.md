---
title: 'Instrukcje: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 6bc1e74e4ae288adcbb2890dda6ab4e4534802a0
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865661"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Instrukcje: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild
  Kompilacji, czyszczenia i sprawdzanie poprawności pakietu programu SharePoint (*.wsp*) przy użyciu wiersza polecenia zadania programu MSBuild na komputerze deweloperskim. Te polecenia umożliwia również Automatyzowanie procesu kompilacji za pomocą programu Team Foundation Server na komputerze kompilacji.  
  
## <a name="build-a-sharepoint-package"></a>Tworzenie pakietu programu SharePoint  
  
#### <a name="to-build-a-sharepoint-package"></a>Aby utworzyć pakiet programu SharePoint  
  
1.  Na Windows **Start** menu, wybierz **wszystkie programy** > **Akcesoria** > **polecenia**.  
  
2.  Przejdź do katalogu, w którym znajduje się projekt programu SharePoint.  
  
3.  Wprowadź następujące polecenie, aby utworzyć pakiet dla projektu. Zastąp *ProjectFileName* nazwą projektu.  
  
    ```cmd  
    msbuild /t:Package ProjectFileName  
    ```  
  
     Na przykład można uruchomić jeden z poniższych poleceń, aby utworzyć projekt programu SharePoint o nazwie ListDefinition1 pakiet.  
  
    ```cmd  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## <a name="clean-a-sharepoint-package"></a>Wyczyść pakietu programu SharePoint  
  
#### <a name="to-clean-a-sharepoint-package"></a>Aby wyczyścić pakietu programu SharePoint  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Przejdź do katalogu, w którym znajduje się projekt programu SharePoint.  
  
3.  Wprowadź następujące polecenie, aby wyczyścić pakietu dla projektu. Zastąp *ProjectFileName* nazwą projektu.  
  
    ```cmd  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     Na przykład można uruchomić jedną z poniższych poleceń, aby wyczyścić projektu programu SharePoint o nazwie ListDefinition1.  
  
    ```cmd  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## <a name="validate-a-sharepoint-package"></a>Sprawdzanie poprawności pakietu programu SharePoint  
  
#### <a name="to-validate-a-sharepoint-package"></a>Aby sprawdzić poprawność pakietu programu SharePoint  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Przejdź do katalogu, w którym znajduje się projekt programu SharePoint.  
  
3.  Wprowadź następujące polecenie, aby zweryfikować pakietu dla projektu. Zastąp *ProjectFileName* nazwą projektu.  
  
    ```cmd  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     Na przykład można uruchomić jedną z poniższych poleceń, aby sprawdzić projekt programu SharePoint o nazwie ListDefinition1.  
  
    ```cmd  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## <a name="set-properties-in-a-sharepoint-package"></a>Ustawianie właściwości w pakiecie programu SharePoint  
  
#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Do ustawiania właściwości w pakiecie programu SharePoint  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Przejdź do katalogu, w którym znajduje się projekt programu SharePoint.  
  
3.  Wprowadź następujące polecenie, aby ustawić właściwość pakietu dla projektu. Zastąp *PropertyName* z właściwościami, który chcesz ustawić.  
  
    ```cmd  
    msbuild /property:PropertyName=Value  
    ```  
  
     Na przykład można uruchomić następujące polecenie, aby ustawić poziom ostrzeżeń.  
  
    ```cmd  
    msbuild /property:WarningLevel = 2  
    ```  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie funkcji SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Instrukcje: Dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Instrukcje: Dodawanie i usuwanie elementów do funkcji SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
