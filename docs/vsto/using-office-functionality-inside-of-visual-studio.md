---
title: Użyj funkcji pakietu Office w Visual Studio
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
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628666"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Użyj funkcji pakietu Office w Visual Studio
  Podczas tworzenia projektu na poziomie dokumentu, dokument i skojarzonej aplikacji znajdują się w programie Visual Studio umożliwiające projektowanie i współpracować bezpośrednio z dokumentu. W przypadku programu Microsoft Office aplikacji Otwórz w programie Visual Studio zazwyczaj działa zgodnie z oczekiwaniami. Jednak niektóre funkcje aplikacji jest inny lub niedostępny.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>Ochrona dokumentu
 Microsoft Office Word i Microsoft Office Excel oferują funkcje ochrony, których można użyć w swoich projektach dokumentu. Jednak jeśli dokument jest chroniony dokument jest otwarty w programie Visual Studio, go może uniemożliwić wprowadzanie pewnych zmian w projekcie. Aby uzyskać więcej informacji, zobacz [dokumentu ochrona w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md).

## <a name="information-rights-management"></a>Zarządzanie prawami do informacji
 Zarządzanie prawami do informacji (IRM) jest dostępna w programie Microsoft Office Word i Microsoft Office Excel. IRM może pomóc w zapobieganiu nieuprawnionym osobom z wyświetlania lub zmieniania informacji poufnych. Jednak usługi IRM można również uniemożliwić Twój kod działa. Aby uzyskać więcej informacji, zobacz [Zarządzanie prawami do informacji i przegląd rozszerzeń kodu zarządzanego](../vsto/information-rights-management-and-managed-code-extensions-overview.md).

## <a name="password-protection"></a>Ochrona za pomocą hasła
 Tak, aby nie można otworzyć przez osobę, która nie zna hasło można ustawić dokumentów programu Microsoft Office Word i skoroszytów programu Microsoft Office Excel. Ochrona za pomocą hasła różni się w programach Word i Excel i może mieć wpływ na procesie tworzenia aplikacji. Aby uzyskać więcej informacji, zobacz [ochrona za pomocą hasła w dokumentach pakietu Office](../vsto/password-protection-on-office-documents.md).

## <a name="see-also"></a>Zobacz także
- [Ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md)
- [Zarządzanie prawami do informacji i przegląd rozszerzeń kodu zarządzanego](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Ochrona za pomocą hasła w dokumentach pakietu Office](../vsto/password-protection-on-office-documents.md)
- [Instrukcje: Otwieranie rozwiązań pakietu Office bez uruchamiania kodu](../vsto/how-to-open-office-solutions-without-running-code.md)
