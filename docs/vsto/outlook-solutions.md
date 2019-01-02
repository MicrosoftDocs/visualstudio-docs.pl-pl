---
title: rozwiązania programu Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6c1849a832bcc2bda8ea63b9939968ea44f5cd5b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868699"
---
# <a name="outlook-solutions"></a>rozwiązania programu Outlook
  Program Visual Studio udostępnia szablony projektów, służących do tworzenia dodatków narzędzi VSTO dla programu Microsoft Office Outlook. Za pomocą dodatków narzędzi VSTO dla programów Automatyzacja programu Outlook, Rozszerz funkcje programu Outlook lub dostosowywanie interfejsu użytkownika (UI) programu Outlook. Aby uzyskać więcej informacji na temat dodatków narzędzi VSTO zobacz [architektury VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Zainteresowanych opracowywaniem rozwiązań, które rozszerzają możliwości pakietu Office w [wiele platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatki pakietu Office mieć o niewielkich rozmiarach, w porównaniu do dodatków narzędzi VSTO dla programów i rozwiązań, a następnie utworzyć je przy użyciu niemal dowolnej technologii, takich jak HTML5, JavaScript, CSS3 i XML programowanie dla sieci web.  
  
## <a name="create-an-outlook-vsto-add-in-project"></a>Tworzenie narzędzi VSTO dla programów Outlook dodatku projektu  
 Tworzenie projektów programu Outlook przy użyciu **dodatku programu Outlook** szablonu projektu w **nowy projekt** okno dialogowe. Ten szablon zawiera odwołania do zestawów wymagane i pliki projektu.  
  
 Aby uzyskać więcej informacji o sposobie tworzenia projektu dodatku narzędzi VSTO dla programów, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Aby uzyskać więcej informacji na temat szablonów projektu, zobacz [Przegląd szablony projektu pakietu Office](../vsto/office-project-templates-overview.md).  
  
## <a name="outlook-vsto-add-in-programming-model"></a>Program Outlook dodatku narzędzi VSTO model programowania  
 Podczas tworzenia projektu dodatku narzędzi VSTO dla programu Outlook, program Visual Studio generuje klasę o nazwie `ThisAddIn`, która jest podstawą rozwiązania. Ta klasa stanowi punkt wyjścia do pisania kodu, a także udostępnia model obiektu Outlook do dodatku narzędzi VSTO dla programów.  
  
 Aby uzyskać więcej informacji na temat `ThisAddIn` klasy i inne funkcje, które można używać w dodatku narzędzi VSTO dla programów, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automate-outlook-by-using-the-outlook-object-model"></a>Automatyzowanie programu Outlook przy użyciu modelu obiektów programu Outlook  
 Model obiektu Outlook uwidacznia wiele typów, których można użyć do zautomatyzowania programu Outlook. Te typy umożliwiają pisanie kodu w celu wykonywania typowych zadań:  
  
- Programowe tworzenie i wysyłanie wiadomości e-mail.  
  
- Wyślij nowe wezwania na spotkanie.  
  
- Wyszukiwanie elementów w folderach programu Outlook.  
  
  Aby uzyskać więcej informacji, zobacz [model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md).  
  
## <a name="customize-the-user-interface-of-an-outlook-application"></a>Dostosowywanie interfejsu użytkownika w aplikacji Outlook  
  
|Zadanie|Więcej informacji|  
|----------|--------------------------|  
|Dodaj niestandardowe karty do wstążki Inspektor programu Outlook.|[Wstążka — omówienie](../vsto/ribbon-overview.md)|  
|Dodaj niestandardowe grupy do wbudowanej karty w Inspektorze programu Outlook.|[Instrukcje: Dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)|  
|Dodawanie niestandardowego okienka zadań wyświetlonym w Inspektor programu Outlook|[Niestandardowe okienka zadań](../vsto/custom-task-panes.md).|  
|Dodawanie regionu formularza, który rozszerza lub zamienia istniejące formularzy programu Outlook.|[Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)|  
  
 Aby uzyskać więcej informacji na temat dostosowywania interfejsu użytkownika programu Outlook i inne aplikacje Microsoft Office, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)|Przegląd obiektów, które są dostarczane przez model obiektów programu Outlook.|  
|[Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)|W tym artykule wyjaśniono narzędzi dostarczanych przez Visual Studio, które ułatwiają służących do projektowania, opracowywania i debugowania regionów formularzy.|  
|[Przewodnik: Tworzenie swojej pierwszej dodatku narzędzi VSTO dla programu Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Pokazuje sposób tworzenia dodatku narzędzi VSTO dla programu Microsoft Office Outlook.|  
|[Program Outlook 2010 w rozwój pakietu Office](http://go.microsoft.com/fwlink/?LinkId=199013)|Obszar biblioteki MSDN, gdzie można znaleźć artykuły i dokumentacji o tworzeniu rozwiązania programu Outlook (nie odnoszą się do rozwoju pakietu Office przy użyciu programu Visual Studio).|  
