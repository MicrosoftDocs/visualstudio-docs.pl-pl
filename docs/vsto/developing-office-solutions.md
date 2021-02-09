---
title: Opracowywanie rozwiązań pakietu Office
description: Dowiedz się, jak projektować projekt przy użyciu narzędzi Office Developer Tools w programie Visual Studio. Dowiedz się również, jak rozpocząć implementację kodu i niestandardowego interfejsu użytkownika.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 012f08b4a4a8364d278322b7fe057231183fa233
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897592"
---
# <a name="develop-office-solutions"></a>Opracowywanie rozwiązań pakietu Office
  Po zaprojektowaniu projektu przy użyciu narzędzi deweloperskich pakietu Office w programie Visual Studio i skonfigurowania plików projektu można rozpocząć skoncentrowanie się na implementowaniu kodu i niestandardowego interfejsu użytkownika.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="office-solutions-programming-model"></a>Model programowania rozwiązań pakietu Office
 Model obiektów pakietu Office uwidacznia różne obiekty, dla których można programować. Za każdym razem, gdy program jest wdrażany za pomocą kodu zarządzanego, napisać kod, który używa typów w podstawowych zestawach międzyoperacyjnych pakietu Office. W rozwiązaniach tworzonych przy użyciu szablonów projektu pakietu Office w programie Visual Studio można napisać kod bezpośrednio na wygenerowane klasy w projekcie. Aby uzyskać więcej informacji, zobacz [pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md).

## <a name="program-different-types-of-office-solutions"></a>Programowanie różnych typów rozwiązań pakietu Office
 Typ tworzonego rozwiązania określa funkcje, których można użyć w projekcie. Na przykład można dodać kontrolki Windows Forms i rozszerzone formanty pakietu Office (nazwane *kontrolki hosta*) do dostosowania na poziomie dokumentu, przeciągając elementy z **przybornika** w programie Visual Studio w czasie projektowania. Jeśli jednak tworzysz dodatek narzędzi VSTO, możesz dodać tylko te rodzaje kontrolek do dokumentów w czasie wykonywania, pisząc kod.

 Więcej informacji o funkcjach specyficznych dla różnych typów rozwiązań znajduje się w następujących tematach:

- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)

- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md).

- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

  Informacje w tle ułatwiające zaplanowanie rozwiązań i procedur związanych z pakietem Office w celu ułatwienia tworzenia projektów można znaleźć w temacie [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)|Opisuje różne aspekty pisania kodu w rozwiązaniach pakietu Office.|
|[Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)|Zawiera omówienie modelu programowania dodatków narzędzi VSTO i powiązanych zadań programistycznych.|
|[Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)|Zawiera omówienie modelu programowania dostosowań na poziomie dokumentu i powiązanych zadań programistycznych.|
|[Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)|Opisuje różne sposoby dostosowywania interfejsu użytkownika aplikacji pakietu Office przy użyciu dodatków narzędzi VSTO i dostosowań na poziomie dokumentu.|
|[Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)|Opisuje różne sposoby pracy z danymi w rozwiązaniach pakietu Office, takie jak Powiązywanie danych z kontrolkami i buforowanie danych w dostosowywaniu na poziomie dokumentu.|
|[Jak automatyczne zapisywanie w rozwiązaniach pakietu Office](./how-autosave-impacts-office-solutions.md)|Opisuje zmiany, które mogą być konieczne w przypadku rozwiązań pakietu Office po włączeniu automatycznego zapisywania.|
|[Rozwiązywanie problemów z rozwiązaniami pakietu Office](../vsto/troubleshooting-office-solutions.md)|Zawiera wskazówki dotyczące rozwiązywania typowych problemów, które mogą wystąpić podczas tworzenia rozwiązań pakietu Office.|
|[Obsługa wątkowości w pakiecie Office](../vsto/threading-support-in-office.md)|Zawiera omówienie pracy z wieloma wątkami w rozwiązaniach pakietu Office.|
|[Ułatwienia dostępu w projektach pakietu Office](../vsto/accessibility-in-office-projects.md)|Zawiera opis funkcji ułatwień dostępu dostępnych w rozwiązaniach pakietu Office.|

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Tworzenie i modyfikowanie właściwości dokumentu niestandardowego](../vsto/how-to-create-and-modify-custom-document-properties.md)
- [Instrukcje: odczytywanie i zapisywanie właściwości dokumentu](../vsto/how-to-read-from-and-write-to-document-properties.md)
- [Instrukcje: kierowanie wielojęzycznego interfejsu użytkownika pakietu Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)
- [Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)
- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla projektu](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)
- [Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
