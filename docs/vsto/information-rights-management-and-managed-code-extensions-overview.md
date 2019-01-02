---
title: Zarządzanie prawami do informacji i przegląd rozszerzeń kodu zarządzanego
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a2020221ee086b23a8621112122acffb11beef62
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823833"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Zarządzanie prawami do informacji i przegląd rozszerzeń kodu zarządzanego
  Program Microsoft Office Word i Microsoft Office Excel umożliwiają zarządzanie prawami informacji (IRM), funkcja, która może pomóc uniknąć nieupoważnione osoby z wyświetlania lub zmieniania informacji poufnych. Aby uzyskać szczegółowe informacje o tym, jak działa Zarządzanie prawami do informacji zobacz Pomoc w określonej aplikacji pakietu Office.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="run-code-behind-documents-with-restricted-permissions"></a>Uruchamianie kodu w tle dokumentów z ograniczonymi uprawnieniami  
 Jeśli Twoje rozwiązanie zawiera dokument lub skoroszyt, który używa usługi IRM, domyślnie, Word i Excel nie zezwalają na jakiegokolwiek kodu do uruchomienia. Jeśli autor dokumentu lub mieć uprawnienie Pełna kontrola, można zmienić domyślne tak, aby Twoje rozwiązanie działa. Aby uzyskać więcej informacji, zobacz [jak: Zezwalanie kodu do uruchamiania w tle dokumentów z ograniczonymi uprawnieniami](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 IRM uniemożliwia korzystanie z <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> można pobrać lub manipulowania danymi, które są buforowane w dokumencie.  
  
## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Użytkownicy końcowi, aby ograniczyć uprawnienia do dokumentów, które używają rozszerzenia kodu zarządzanego  
 Aby ograniczyć uprawnienia, każdy, kto ma dostęp Pełna kontrola do dokumentu lub skoroszytu w rozwiązaniu korzystać z funkcji IRM. Na przykład, jeśli użytkownik końcowy w dziale księgowości korzysta z rozwiązania, które automatycznie wypełni arkusza z danymi z bazy danych, ten użytkownik może chcieć zezwolić na dostęp zmiany tylko dla osób w dziale lub jej i dostęp do odczytu do innych osób. Gdy użytkownik dodaje ograniczonych uprawnień, domyślnie nie można uruchomić kod związany z arkusza i arkusza nie zostanie wypełniony danymi.  
  
 Aby rozwiązać ten problem, dostęp Pełna kontrola do dokumentu lub skoroszytu zmienić domyślne ustawienia uprawnień, aby zezwolić na dostęp programistyczny do modelu obiektów. Aby uzyskać więcej informacji, zobacz [jak: Zezwalanie kodu do uruchamiania w tle dokumentów z ograniczonymi uprawnieniami](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md)   
 [Ochrona za pomocą hasła w dokumentach pakietu Office](../vsto/password-protection-on-office-documents.md)   
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)  
