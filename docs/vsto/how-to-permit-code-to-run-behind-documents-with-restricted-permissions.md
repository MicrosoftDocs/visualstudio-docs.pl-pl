---
title: Zezwalaj na uruchamianie kodu w tle z ograniczonymi uprawnieniami
description: Dowiedz się, jak można zezwolić na uruchamianie kodu w tle dokumentów z ograniczonymi uprawnieniami przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1a65e99712658567996598d2190447ff09cf9b05
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888891"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Instrukcje: Zezwalanie na uruchamianie kodu w tle dokumentów z ograniczonymi uprawnieniami
  Za pomocą funkcji Rights Management informacji (IRM) Microsoft Office można ograniczyć uprawnienia do dokumentu lub skoroszytu. Domyślnie nie można uruchamiać kodu związanego z Microsoft Office ograniczonym dokumentem programu Word lub Microsoft Office skoroszycie programu Excel. Można zmienić wartość domyślną, aby rozszerzenia kodu zarządzanego mogły uzyskać dostęp do modelu obiektów, a Twoje rozwiązanie będzie działało.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Musisz być autorem dokumentu lub skoroszytu lub mieć dostęp Pełna kontrola, aby móc zmieniać ustawienia uprawnień.

## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Aby zezwolić na uruchamianie kodu w tle dokumentów z ograniczonymi uprawnieniami

1. Otwórz dokument lub skoroszyt w programie Word lub Excel.

2. Kliknij kartę **plik** , wskaż polecenie **Przygotuj**, wskaż polecenie **Ogranicz uprawnienia**, a następnie kliknij przycisk **dostęp z ograniczeniami**.

   > [!NOTE]
   > Przy pierwszym użyciu zostanie wyświetlony monit o zainstalowanie klienta Rights Management systemu Windows. Po zainstalowaniu klienta programu może być konieczne powtórzenie kroków.

3. W oknie dialogowym **uprawnienia** wybierz opcję **Ogranicz uprawnienie do tego dokumentu**, a następnie kliknij przycisk **więcej opcji**.

4. W obszarze **dodatkowe uprawnienia dla użytkowników** wybierz pozycję **dostęp do zawartości programowo**.

   Program Word lub Excel zezwoli programistycznemu dostępowi do modelu obiektów.

## <a name="see-also"></a>Zobacz też
- [Zarządzanie prawami do informacji i rozszerzenia kodu zarządzanego — Omówienie](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md)
- [Ochrona hasłem w dokumentach pakietu Office](../vsto/password-protection-on-office-documents.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
