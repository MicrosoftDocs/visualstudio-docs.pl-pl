---
title: 'Instrukcje: Zezwalanie kodu do uruchamiania w tle dokumentów z ograniczonymi uprawnieniami'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- IRM [Office development in Visual Studio]
- code [Office development in Visual Studio], running behind restricted documents
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a5e65c086b69a712b2df5a1a12939b41828ad198
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445343"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Instrukcje: Zezwalanie kodu do uruchamiania w tle dokumentów z ograniczonymi uprawnieniami
  Aby ograniczyć uprawnienia do dokumentu lub skoroszytu, można użyć funkcji zarządzania prawami do informacji (IRM) pakietu Microsoft Office. Domyślnie kod związany z ograniczeniami dokumentu Microsoft Office Word lub skoroszytu programu Microsoft Office Excel nie ma zezwolenia na uruchomienie. Domyślne można zmienić tak, aby rozszerzenia kodu zarządzanego mogą uzyskiwać dostęp do modelu obiektów, a rozwiązania będą działać.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Musi być autorem dokument lub skoroszyt, lub mieć uprawnienie Pełna kontrola, aby można było zmienić ustawienia uprawnień.

## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Aby zezwolić na kod wymagany do uruchomienia w tle dokumentów z ograniczonymi uprawnieniami

1. Otwórz dokument lub skoroszyt w programie Word lub Excel.

2. Kliknij przycisk **pliku** kartę, wskaż opcję **przygotowanie**, wskaż polecenie **Ogranicz uprawnienia**, a następnie kliknij przycisk **ograniczony dostęp**.

   > [!NOTE]
   > Przy pierwszym użyciu monit o zainstalowanie klienta usługi Windows Rights Management. Po zainstalowaniu klienta, może być konieczne czynności.

3. W **uprawnienie** okno dialogowe, wybierz opcję **Ogranicz uprawnienia do tego dokumentu**, a następnie kliknij przycisk **więcej opcji**.

4. W obszarze **dodatkowe uprawnienia dla użytkowników**, wybierz opcję **programowy dostęp do zawartości**.

   Word lub Excel będzie zezwalać na dostęp programowy do modelu obiektów.

## <a name="see-also"></a>Zobacz także
- [Zarządzanie prawami do informacji i przegląd rozszerzeń kodu zarządzanego](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md)
- [Ochrona za pomocą hasła w dokumentach pakietu Office](../vsto/password-protection-on-office-documents.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
- [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)
