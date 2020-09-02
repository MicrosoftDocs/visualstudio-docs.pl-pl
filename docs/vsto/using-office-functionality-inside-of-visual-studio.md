---
title: Korzystanie z funkcji pakietu Office w programie Visual Studio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c47ed9639a33ecdea3451c63b729d959f6855e5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62982329"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Korzystanie z funkcji pakietu Office w programie Visual Studio
  Podczas tworzenia projektu na poziomie dokumentu dokument i skojarzona aplikacja są hostowane w programie Visual Studio, dzięki czemu można projektować i współpracować bezpośrednio z dokumentem. Gdy aplikacja Microsoft Office jest otwarta w programie Visual Studio, zazwyczaj działa zgodnie z oczekiwaniami. Niektóre funkcje aplikacji są jednak różne lub niedostępne.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>Ochrona dokumentów
 Microsoft Office Word i Microsoft Office Excel oferują funkcje ochrony dokumentów, których można używać w projektach. Jeśli jednak włączono ochronę dokumentów, gdy dokument jest otwarty w programie Visual Studio, może to uniemożliwić Dokonywanie pewnych zmian w projekcie. Aby uzyskać więcej informacji, zobacz [Ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md).

## <a name="information-rights-management"></a>Zarządzanie prawami do informacji
 Informacje Rights Management (IRM) są dostępne w programach Microsoft Office Word i Microsoft Office Excel. Usługa IRM może pomóc uniemożliwić nieuprawnionym osobom wyświetlanie lub zmienianie poufnych informacji. Jednak usługa IRM może również uniemożliwić uruchomienie kodu. Aby uzyskać więcej informacji, zobacz [Omówienie usługi zarządzania prawami do informacji i rozszerzenia kodu zarządzanego](../vsto/information-rights-management-and-managed-code-extensions-overview.md).

## <a name="password-protection"></a>Ochrona hasłem
 Można ustawić Microsoft Office dokumenty programu Word i Microsoft Office skoroszyty programu Excel, aby nie mogły zostać otwarte przez kogoś, kto nie zna hasła. Ochrona hasłem jest obsługiwana inaczej w programach Word i Excel i może mieć wpływ na proces opracowywania. Aby uzyskać więcej informacji, zobacz [Ochrona hasłem w dokumentach pakietu Office](../vsto/password-protection-on-office-documents.md).

## <a name="see-also"></a>Zobacz też
- [Ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md)
- [Zarządzanie prawami do informacji i rozszerzenia kodu zarządzanego — Omówienie](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Ochrona hasłem w dokumentach pakietu Office](../vsto/password-protection-on-office-documents.md)
- [Instrukcje: otwieranie rozwiązań pakietu Office bez uruchamiania kodu](../vsto/how-to-open-office-solutions-without-running-code.md)
