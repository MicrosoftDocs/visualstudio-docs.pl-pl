---
title: Opracowywania rozwiązań pakietu Office
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1aa7be95b0812b27c302500bd166abcb00c7089d
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874533"
---
# <a name="develop-office-solutions"></a>Opracowywania rozwiązań pakietu Office
  Po Projektowanie projektu przy użyciu narzędzi Office developer tools w programie Visual Studio i konfigurowanie plików projektu, możesz rozpocząć koncentrować się na realizacji kodu i niestandardowego interfejsu użytkownika (UI).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Zainteresowanych opracowywaniem rozwiązań, które rozszerzają możliwości pakietu Office w [wiele platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatki pakietu Office mieć o niewielkich rozmiarach, w porównaniu do dodatków narzędzi VSTO dla programów i rozwiązań, a następnie utworzyć je przy użyciu niemal dowolnej technologii, takich jak HTML5, JavaScript, CSS3 i XML programowanie dla sieci web.  
  
## <a name="office-solutions-programming-model"></a>Model programowania rozwiązań dla pakietu Office  
 Model obiektów programu pakietu Office ujawnia różnych obiektów, które można programować względem. Zawsze, gdy programujesz rozwiązań pakietu Office przy użyciu kodu zarządzanego, możesz napisać kod, który korzysta z typów podstawowych zestawów międzyoperacyjnych pakietu Office. W przypadku rozwiązań tworzonych przy użyciu szablonów projektów pakietu Office w programie Visual Studio możesz także napisać kod bezpośrednio w odniesieniu do wygenerowanych klas w projekcie. Aby uzyskać więcej informacji, zobacz [pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="program-different-types-of-office-solutions"></a>Program różnych typów rozwiązań dla pakietu Office  
 Typ rozwiązania, które tworzysz Określa funkcje, których można użyć w projekcie. Na przykład można dodać kontrolki Windows Forms oraz rozszerzone pakietu Office (o nazwie *hostowania kontrolek*) do dostosowywania na poziomie dokumentu przez przeciąganie elementów z **przybornika** w programie Visual Studio w czasie projektowania . Jednak tworzenia dodatku narzędzi VSTO tylko dodaniem tego rodzaju formantów do dokumentów w czasie wykonywania, przez napisanie kodu.  
  
 Aby uzyskać więcej informacji o funkcjach, które są specyficzne dla różnych rozwiązań zobacz następujące tematy:  
  
- [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md).  
  
- [Program dostosowań poziomu dokumentu](../vsto/programming-document-level-customizations.md).  
  
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
  Aby uzyskać ogólne informacje pomóc Ci zaplanować procedury ułatwiające tworzenie projektów i rozwiązań dla pakietu Office, zobacz [projektowania i tworzenia rozwiązań dla pakietu Office](../vsto/designing-and-creating-office-solutions.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)|W tym artykule opisano różne aspekty pisany w rozwiązaniach pakietu Office.|  
|[Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)|Omówienie modelu programowania dodatków narzędzi VSTO dla programów i powiązanych zadań programistycznych.|  
|[Program dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)|Omówienie modelu programowania dostosowań na poziomie dokumentu i powiązanych zadań programistycznych.|  
|[Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)|W tym artykule opisano różne sposoby, które można dostosować aplikacji interfejsu użytkownika pakietu Office za pomocą dodatków narzędzi VSTO dla programów i dostosowań na poziomie dokumentu.|  
|[Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)|W tym artykule opisano różne sposoby, za pomocą którego można używać z danymi w rozwiązaniach pakietu Office, takich jak powiązywanie danych z kontrolkami i buforowanie danych w dostosowaniach na poziomie dokumentu.|  
|[Wpływ automatycznego zapisywania na rozwiązania pakietu Office](./how-autosave-impacts-office-solutions.md)|W tym artykule opisano dostosowań, który użytkownik może być konieczne do rozwiązań pakietu Office po włączeniu zapisywania.|
|[Rozwiązywanie problemów z rozwiązań pakietu Office](../vsto/troubleshooting-office-solutions.md)|Zawiera wskazówki dotyczące rozwiązywania typowych problemów, które można napotkać podczas tworzenia rozwiązań dla pakietu Office.|  
|[Obsługa wątkowości w Office](../vsto/threading-support-in-office.md)|Zawiera omówienie pracy z wieloma wątkami w rozwiązaniach pakietu Office.|  
|[Ułatwienia dostępu w projektach pakietu Office](../vsto/accessibility-in-office-projects.md)|Opisuje funkcje ułatwień dostępu, które są dostępne w rozwiązaniach pakietu Office.|  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Tworzenie i modyfikowanie właściwości niestandardowego dokumentu](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [Instrukcje: Odczytywanie i zapisywanie właściwości dokumentów](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [Instrukcje: Docelowy urząd wielojęzyczny interfejs użytkownika](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Przewodnik: Tworzenie swojej pierwszej dodatku narzędzi VSTO dla programu Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Przewodnik: Tworzenie swojej pierwszej dodatku narzędzi VSTO dla projektu](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
