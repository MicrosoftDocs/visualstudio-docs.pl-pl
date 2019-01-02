---
title: Rozszerzanie pakowania i wdrażania SharePoint | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 54c735bf0ab534e042e595fd12864a06dcf0a30f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916882"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>Rozszerzanie pakowania i wdrażania SharePoint
  Możesz rozszerzyć pakowania i proces wdrażania dla projektów programu SharePoint.
  
## <a name="create-deployment-steps"></a>Utwórz kroki związane z wdrażaniem
 Podczas wdrażania projektu programu SharePoint [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] wykonuje serię kroków wdrażania. Visual Studio zawiera kroki wdrażania wbudowanych w przypadku wielu zadań, takich jak wycofywanie i dodawanie rozwiązań. Jednak można również utworzyć własne kroki wdrażania.  
  
 Aby wskazówki, który demonstruje, jak utworzyć kroku wdrożenia, zobacz [instruktażu: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="create-deployment-configurations"></a>Tworzenie konfiguracji wdrożenia
 Konfiguracja wdrożenia jest zestaw kroków wdrażania, który jest wykonywany dla danego projektu, ale mogą mieć wpływ na wszystkich elementów projektu programu SharePoint. Każdej konfiguracji wdrożenia zawiera jeden zestaw kroków wykonanych podczas wdrażania projektu, a kolejny zestaw, który jest wykonywany, gdy projekt jest wycofana. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] obejmuje dwie konfiguracje wdrożenia wbudowanych, ale można także tworzyć własne. Podczas tworzenia konfiguracji wdrożenia może zawierać kroki wdrażania wbudowanych i kroków wdrażania, które tworzysz.  
  
 Aby wskazówki, który demonstruje, jak utworzyć konfigurację wdrożenia, zobacz [instruktażu: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Uruchamianie kodu, gdy rozwiązania programu SharePoint jest wdrożony lub wycofany
 Możesz obsłużyć zdarzenia na wykonywanie dodatkowych zadań, gdy rozwiązania programu SharePoint jest wdrożony lub wycofany. Program Visual Studio wywołuje zdarzenia, które może obsłużyć w następujących scenariuszach:  
  
-   Przed i po każdym wdrożeniu krok jest wykonywany dla elementu projektu programu SharePoint. Aby uzyskać więcej informacji, zobacz [jak: Uruchamianie kodu, gdy są wykonywane kroki związane z wdrażaniem](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).  
  
-   Przed i po projektu programu SharePoint jest wdrożony lub wycofany. Aby uzyskać więcej informacji, zobacz [jak: Uruchamianie kodu, podczas projektu programu SharePoint jest wdrożony lub wycofany](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).  
  
## <a name="handle-deployment-conflicts"></a>Obsługa konfliktów wdrożenia
 Niektóre typy elementów projektu programu SharePoint, w tym moduły, części sieci Web, przejrzenia listy wystąpień i typów zawartości, podaj Rozwiązywanie konfliktów wdrażania wbudowanych. Podczas wdrażania rozwiązania, który zawiera jeden z tych elementów projektu programu Visual Studio najpierw sprawdza, czy plik istnieje już w witrynie programu SharePoint przy użyciu tej samej nazwie, adres URL lub identyfikator jako plik na element, który jest wdrażany. W przypadku konfliktu, program Visual Studio może automatycznie rozwiązać konfliktu lub monitować umożliwia ustalenie, czy zainstalowano oprogramowania Visual Studio rozwiązać konflikt, lub przycisk Anuluj, wdrożenie. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z pakowaniem i wdrażaniem SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
 Możesz rozszerzyć tę funkcję, podając własny kod, który sprawdza i rozwiązuje konflikty wdrażania. Aby uzyskać więcej informacji, zobacz [jak: Obsługa konfliktów wdrożenia](../sharepoint/how-to-handle-deployment-conflicts.md).  
  
## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Uruchamianie operacji wiersza polecenia przed lub po wdrożeniu projektu
 Jeśli chcesz uruchomić operacji wiersza polecenia po wdrożeniu rozwiązania programu SharePoint, możesz ustawić <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> właściwości <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiektu. Visual Studio wykonuje polecenia przed i po wdrożeniu projektu.  
  
 W niektórych przypadkach może zostać wyświetlony konflikty wdrażania. Istnieje kilka różnych sposobów, aby rozwiązać konflikty. Aby uzyskać więcej informacji, zobacz [SharePoint Rozwiązywanie problemów z pakowaniem i wdrażaniem](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
## <a name="customize-validation-rules"></a>Dostosowywanie reguł sprawdzania poprawności
 Przed wdrożeniem pakietu rozwiązania (wsp), można utworzyć funkcji niestandardowych i pakietu reguł sprawdzania poprawności, aby sprawdzić, czy funkcja lub pakietu jest prawidłowa. Na przykład możesz zgłaszać informacje, ostrzeżenia lub błędy dla deweloperów, aby ułatwić rozwiązywanie problemów z weryfikacji. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie funkcji niestandardowej oraz pakiet reguł sprawdzania poprawności dla rozwiązań SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## <a name="see-also"></a>Zobacz także
 [Instrukcje: Uruchamianie kodu, gdy są wykonywane kroki związane z wdrażaniem](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Instrukcje: Tworzenie funkcji niestandardowej oraz pakiet reguł sprawdzania poprawności dla rozwiązań SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)   
 [Rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
