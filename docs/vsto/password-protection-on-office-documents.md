---
title: Ochrona hasłem w dokumentach pakietu Office
description: Dowiedz się, jak ustawić hasło dla dokumentów programu Microsoft Word i skoroszytów programu Excel, aby nie mogły być otwierane przez nieautoryzowanych użytkowników.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2cc320baf310af0ec2b4cdd84fabff951b2a9cb2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885290"
---
# <a name="password-protection-on-office-documents"></a>Ochrona hasłem w dokumentach pakietu Office
  Istnieje możliwość ustawienia hasła Microsoft Office dokumentów programu Word i Microsoft Office skoroszytów programu Excel, aby nie mogły zostać otwarte przez kogoś, kto nie zna hasła. Ta opcja jest nazywana **hasłem przy otwarciu**.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Możesz tworzyć projekty na poziomie dokumentu przy użyciu istniejących dokumentów i skoroszytów z włączonym **hasłem otwartym** . Zachowanie w programie Visual Studio różni się w przypadku dokumentów programów Word i Excel z włączonym **hasłem po otwarciu** .

 Aby uzyskać informacje na temat włączania **hasła przy otwieraniu**, zobacz Pomoc w programie Word lub Excel.

## <a name="behavior-of-excel-and-word"></a>Zachowanie programów Excel i Word
 Za każdym razem, gdy otworzysz skoroszyt programu Excel w programie Visual Studio, który ma **hasło przy włączonej otwartej** , program Excel poprosi o hasło. Podczas kompilowania rozwiązania zostanie wyświetlony monit o podanie hasła, ponieważ dokument jest otwierany podczas kompilacji.

 Przy pierwszym otwarciu dokumentu programu Word w programie Visual Studio z włączonym **hasłem przy otwartym** programie Word zostanie wyświetlony komunikat z prośbą o hasło. Po pomyślnym wprowadzeniu hasła do dokumentu zostanie usunięte **hasło z okna otwieranie** i otwarcie dokumentu nie będzie wymagało hasła. Jeśli chcesz, aby dokument w rozwiązaniu wymagał hasła przed jego otwarciem, musisz włączyć **hasło podczas otwierania** po zakończeniu kompilacji i przed wdrożeniem rozwiązania.

## <a name="see-also"></a>Zobacz też
- [Ochrona dokumentów w rozwiązaniach na poziomie dokumentu](../vsto/document-protection-in-document-level-solutions.md)
- [Zarządzanie prawami do informacji i rozszerzenia kodu zarządzanego — Omówienie](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Instrukcje: Zezwalanie na uruchamianie kodu w tle dokumentów z ograniczonymi uprawnieniami](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
