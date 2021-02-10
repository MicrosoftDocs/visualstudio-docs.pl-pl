---
title: Rozszerzanie pakowania i wdrażania programu SharePoint | Microsoft Docs
description: Rozwiń pakiet i wdrażanie programu SharePoint. Utwórz kroki wdrażania i konfiguracje. Obsłuż konflikty wdrożenia. Dostosuj reguły sprawdzania poprawności.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cd4967e38738018f9b30365575a2dcb9e8970963
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948755"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>Rozszerzona pakowanie i wdrażanie programu SharePoint
  Można rozłożyć proces tworzenia pakietów i wdrożeń dla projektów programu SharePoint.

## <a name="create-deployment-steps"></a>Tworzenie kroków wdrożenia
 Podczas wdrażania projektu programu SharePoint program [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] wykonuje serię kroków wdrożenia. Program Visual Studio zawiera wbudowane kroki wdrażania dla wielu zadań, takich jak wycofywanie i Dodawanie rozwiązań. Można jednak również utworzyć własne kroki wdrażania.

 Aby zapoznać się z przewodnikiem, który ilustruje sposób tworzenia kroku wdrożenia, zobacz [Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="create-deployment-configurations"></a>Tworzenie konfiguracji wdrożenia
 Konfiguracja wdrożenia to zestaw kroków wdrażania, które są wykonywane dla danego projektu, ale mogą mieć wpływ na wszystkie elementy projektu programu SharePoint. Każda konfiguracja wdrożenia obejmuje jeden zestaw kroków wykonywanych podczas wdrażania projektu oraz inny zestaw, który jest wykonywany podczas wycofywania projektu. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] obejmuje dwie wbudowane konfiguracje wdrażania, ale można również utworzyć własne. Podczas tworzenia konfiguracji wdrożenia można uwzględnić wbudowane kroki wdrażania i etapy wdrażania.

 Aby zapoznać się z przewodnikiem, który pokazuje, jak utworzyć konfigurację wdrożenia, zobacz [Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Uruchom kod, gdy rozwiązanie SharePoint zostanie wdrożone lub wycofane
 Można obsługiwać zdarzenia w celu wykonywania dodatkowych zadań, gdy rozwiązanie SharePoint zostanie wdrożone lub wycofane. Program Visual Studio zgłasza zdarzenia, które można obsłużyć w następujących scenariuszach:

- Przed i po wykonaniu każdego kroku wdrożenia dla elementu projektu programu SharePoint. Aby uzyskać więcej informacji, zobacz [How to: Run Code, gdy wykonywane są kroki wdrażania](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).

- Przed i po wdrożeniu lub wycofaniu projektu programu SharePoint. Aby uzyskać więcej informacji, zobacz [How to: Run Code, gdy projekt SharePoint jest wdrożony lub wycofany](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).

## <a name="handle-deployment-conflicts"></a>Obsługa konfliktów wdrożenia
 Niektóre typy elementów projektu programu SharePoint, w tym moduły, składniki Web Part, wystąpienia list i typy zawartości, zapewniają wbudowane rozwiązanie konfliktu wdrożenia. Po wdrożeniu rozwiązania, które zawiera jeden z tych elementów projektu, program Visual Studio najpierw sprawdza, czy plik już istnieje w witrynie programu SharePoint o tej samej nazwie, adresie URL lub IDENTYFIKATORze co plik w elemencie, który jest wdrażany. Jeśli istnieje konflikt, program Visual Studio może automatycznie rozwiązać konflikt lub może monitować o określenie, czy chcesz, aby program Visual Studio rozwiązał konflikt lub anulował wdrożenie. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z pakietami i wdrażaniem programu SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

 Tę funkcję można zwiększyć, dostarczając własny kod, który sprawdza i rozwiązuje konflikty wdrożenia. Aby uzyskać więcej informacji, zobacz [How to: handlee konflikty wdrożenia](../sharepoint/how-to-handle-deployment-conflicts.md).

## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Uruchom operacje wiersza polecenia przed wdrożeniem projektu lub po nim
 Jeśli chcesz uruchomić operację wiersza polecenia podczas wdrażania rozwiązania programu SharePoint, możesz ustawić <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> właściwości i <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiektu. Program Visual Studio wykonuje te polecenia przed wdrożeniem projektu i po nim.

 W niektórych przypadkach mogą wystąpić konflikty wdrożenia. Istnieje kilka różnych sposobów rozwiązywania konfliktów. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z pakietami i wdrażaniem programu SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

## <a name="customize-validation-rules"></a>Dostosuj reguły walidacji
 Przed wdrożeniem pakietu rozwiązań (wsp) można utworzyć niestandardowe reguły sprawdzania poprawności pakietów, aby sprawdzić, czy funkcja lub pakiet są prawidłowe. Można na przykład zgłosić informacje, ostrzeżenia lub błędy do deweloperów, aby ułatwić im Rozwiązywanie problemów z walidacją. Aby uzyskać więcej informacji, zobacz [How to: Create Custom Feature and Package Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: uruchamianie kodu po wykonaniu kroków wdrożenia](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Instrukcje: Tworzenie niestandardowych reguł walidacji pakietu dla rozwiązań SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)
- [Poszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
