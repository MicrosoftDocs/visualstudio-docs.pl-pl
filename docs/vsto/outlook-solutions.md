---
title: rozwiązania programu Outlook
ms.date: 08/14/2019
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 21e6478bb0f02383066a2c63dad1bdaf980a0b5b
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985672"
---
# <a name="outlook-solutions"></a>rozwiązania programu Outlook
  Program Visual Studio zawiera szablony projektów, których można użyć do tworzenia dodatków narzędzi VSTO dla Microsoft Office Outlook. Dodatki VSTO umożliwiają Automatyzowanie programu Outlook, rozszerzenia funkcji programu Outlook lub Dostosowywanie interfejsu użytkownika programu Outlook. Aby uzyskać więcej informacji na temat dodatków narzędzi VSTO, zobacz [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-an-outlook-vsto-add-in-project"></a>Utwórz projekt dodatku VSTO dla programu Outlook
 Utwórz projekty programu Outlook przy użyciu szablonu projektu **dodatku programu Outlook** w oknie dialogowym **Nowy projekt** . Ten szablon zawiera wymagane odwołania do zestawu i pliki projektu.

 Aby uzyskać więcej informacji na temat sposobu tworzenia projektu dodatku VSTO, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Aby uzyskać więcej informacji o szablonach projektów, zobacz [Office Project Templates Overview](../vsto/office-project-templates-overview.md).

## <a name="outlook-vsto-add-in-programming-model"></a>Model programowania dodatku programu Outlook VSTO
 Podczas tworzenia projektu dodatku VSTO programu Outlook program Visual Studio generuje klasę o nazwie `ThisAddIn`, która jest podstawą rozwiązania. Ta klasa udostępnia punkt wyjścia do pisania kodu, a także udostępnia model obiektów programu Outlook do dodatku VSTO.

 Aby uzyskać więcej informacji na temat klasy `ThisAddIn` i innych funkcji, których można użyć w dodatku narzędzi VSTO, zobacz [dodatek narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

## <a name="automate-outlook-by-using-the-outlook-object-model"></a>Automatyzowanie programu Outlook przy użyciu modelu obiektów programu Outlook
 Model obiektów programu Outlook ujawnia wiele typów, których można użyć do automatyzowania programu Outlook. Te typy umożliwiają pisanie kodu w celu wykonywania typowych zadań:

- Programowe tworzenie i wysyłanie wiadomości e-mail.

- Wyślij nowe żądania spotkania.

- Wyszukaj elementy w folderach programu Outlook.

  Aby uzyskać więcej informacji, zobacz temat [Omówienie modelu obiektów programu Outlook](../vsto/outlook-object-model-overview.md).

## <a name="customize-the-user-interface-of-an-outlook-application"></a>Dostosowywanie interfejsu użytkownika aplikacji Outlook

|Zadanie|Więcej informacji|
|----------|--------------------------|
|Dodaj niestandardowe karty do wstążki inspektora programu Outlook.|[Omówienie wstążki](../vsto/ribbon-overview.md)|
|Dodawanie grup niestandardowych do wbudowanej karty w Inspektorze programu Outlook.|[Instrukcje: dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md)|
|Dodawanie niestandardowego okienka zadań wyświetlanego w Inspektorze programu Outlook|[Niestandardowe okienka zadań](../vsto/custom-task-panes.md).|
|Dodaj region formularza, który rozszerza lub zastępuje istniejące formularze programu Outlook.|[Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)|

 Aby uzyskać więcej informacji na temat dostosowywania interfejsu użytkownika programu Outlook i innych aplikacji Microsoft Office, zobacz temat [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Model obiektów programu Outlook — Omówienie](../vsto/outlook-object-model-overview.md)|Zawiera omówienie obiektów dostarczanych przez model obiektów programu Outlook.|
|[Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)|Wyjaśnia Narzędzia udostępniane przez program Visual Studio, które ułatwiają projektowanie, opracowywanie i debugowanie regionów formularzy.|
|[Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Pokazuje, jak utworzyć dodatek narzędzi VSTO dla programu Microsoft Office Outlook.|
|[Outlook 2010 w programowaniu pakietu Office](/previous-versions/office/developer/office-2010/ff458122(v=office.14))|Obszar biblioteki MSDN, w którym można znaleźć artykuły i dokumentację referencyjną dotyczącą opracowywania rozwiązań programu Outlook (niespecyficznych dla rozwoju pakietu Office przy użyciu programu Visual Studio).|
