---
title: Zarządzanie prawami do informacji & rozszerzenia kodu zarządzanego
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 753f3d2da201c67cd86c697eccf7580596a40d6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68872061"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Zarządzanie prawami do informacji i rozszerzenia kodu zarządzanego — Omówienie
  Microsoft Office Word i Microsoft Office Excel udostępniają informacje Rights Management (IRM), funkcję, która może pomóc w zapobieganiu wyświetlaniu lub zmienianiu informacji poufnych przez nieautoryzowane osoby. Aby uzyskać szczegółowe informacje na temat sposobu działania Rights Management informacji, zobacz Pomoc w określonej aplikacji pakietu Office.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="run-code-behind-documents-with-restricted-permissions"></a>Uruchamianie kodu w dokumentach z ograniczonymi uprawnieniami
 Jeśli rozwiązanie zawiera dokument lub skoroszyt korzystający z usługi IRM, domyślnie programy Word i Excel nie zezwalają na uruchamianie żadnego kodu. Jeśli jesteś autorem dokumentu lub masz pełną kontrolę dostępu, możesz zmienić wartość domyślną, aby Twoje rozwiązanie zadziałało. Aby uzyskać więcej informacji, zobacz [jak: Zezwalanie na uruchamianie kodu w tle dokumentów z ograniczonymi uprawnieniami](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

 Usługa IRM uniemożliwia korzystanie z programu <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> do pobierania danych przechowywanych w pamięci podręcznej lub manipulowania nimi.

## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Użytkownicy końcowi ograniczający uprawnienia do dokumentów korzystających z rozszerzeń kodu zarządzanego
 Każda osoba, która ma pełny dostęp do dokumentu lub skoroszytu w rozwiązaniu, może używać usługi IRM do ograniczania uprawnień. Na przykład jeśli użytkownik końcowy w dziale księgowości korzysta z rozwiązania, które automatycznie wypełnia arkusz danymi z bazy danych, może być konieczne zezwolenie na zmianę dostępu tylko do osób w jego dziale i dostęp do odczytu innym osobom. Gdy użytkownik dodaje ograniczone uprawnienia, domyślnie kod związany z arkuszem nie może zostać uruchomiony, a arkusz nie zostanie wypełniony danymi.

 Aby rozwiązać ten problem, ktoś z dostępem Pełna kontrola do dokumentu lub skoroszytu musi zmienić domyślne ustawienia uprawnień, aby zezwolić na dostęp programistyczny do modelu obiektów. Aby uzyskać więcej informacji, zobacz [jak: Zezwalanie na uruchamianie kodu w tle dokumentów z ograniczonymi uprawnieniami](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

## <a name="see-also"></a>Zobacz też
- [Ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md)
- [Ochrona hasłem w dokumentach pakietu Office](../vsto/password-protection-on-office-documents.md)
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
