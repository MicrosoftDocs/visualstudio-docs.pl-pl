---
title: Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word
description: Dowiedz się, co musisz wiedzieć, aby rozpocząć tworzenie dostosowań na poziomie dokumentu dla programu Microsoft Office Word przy użyciu programu Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e9420ab02b5f402dd39e5ca1713b911a10932dfb
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845183"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word
  Jeśli dopiero zaczynasz tworzyć dostosowania na poziomie dokumentu dla programu Microsoft Office Word przy użyciu programu Visual Studio, Oto co należy wiedzieć.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-word-work"></a>Dowiedz się, jak dostosowania na poziomie dokumentu dla programu Word
 Każde utworzone dostosowanie wyrazu opiera się na jednym dokumencie. Aby rozpocząć korzystanie z dostosowania, użytkownik końcowy otwiera dokument lub tworzy dokument przy użyciu szablonu programu Word. Zdarzenia w dokumencie, na przykład przeniesienie kursora do określonych obszarów lub kliknięcie przycisków i elementów menu, może wywołać metody obsługi zdarzeń w zestawie. Gdy dokument zostanie zamknięty, funkcje udostępniane przez dostosowanie nie będą już dostępne w programie Word.

 Aby uzyskać więcej informacji, zobacz [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-word"></a>Tworzenie projektów na poziomie dokumentu dla programu Word
 Aby utworzyć dostosowanie na poziomie dokumentu dla programu Word, użyj szablonu dokumentu programu Word lub szablonu programu Word w oknie dialogowym **Nowy projekt** . Szablony te zawierają wymagane odwołania do zestawów i pliki projektu.

 Aby uzyskać więcej informacji na temat tworzenia projektu na poziomie dokumentu dla programu Word, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Aby uzyskać więcej informacji o szablonach projektów, zobacz [Office Project Templates Overview](../vsto/office-project-templates-overview.md).

## <a name="program-word-documents-by-using-host-items-host-controls"></a>Programowanie dokumentów programu Word przy użyciu elementów hosta formantów hosta
 *Elementy hosta* i *kontrolki hosta* to klasy, które udostępniają model programowania dla dostosowań na poziomie dokumentu.

 Elementy hosta zapewniają punkt wejścia dla kodu i mogą działać jako kontenery dla formantów hosta i formantów Windows Forms. W projektach na poziomie dokumentu dla programu Word element hosta jest reprezentowany przez `ThisDocument` klasę.

 Formanty hosta są oparte na natywnych obiektach programu Word, takich jak kontrolki zawartości, zakładki i węzły XML. Formanty hosta zapewniają podobną funkcjonalność do obiektów natywnego programu Word, ale mają także nowe zdarzenia, obsługę projektanta i funkcję powiązania danych. Są one wyświetlane jako obiekty pierwszej klasy w kodzie projektu i w technologii IntelliSense, które ułatwiają odwoływanie się do określonych obiektów bezpośrednio w kodzie bez konieczności nawigowania po modelu obiektów programu Word.

 Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)

- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)

- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-word"></a>Dostosowywanie interfejsu użytkownika programu Word
 Większość Microsoft Officeych rozwiązań modyfikuje interfejs użytkownika aplikacji pakietu Office, aby zapewnić użytkownikom możliwość współdziałania z rozwiązaniem. Istnieje wiele sposobów modyfikowania interfejsu użytkownika programu Word przy użyciu dostosowania na poziomie dokumentu. Na przykład można dodać kontrolki do wstążki i wyświetlić okienko akcji. Aby uzyskać więcej informacji, zobacz temat [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

 Możesz również otworzyć dokument skojarzony z projektem bezpośrednio w programie Visual Studio. Gdy dokument jest otwarty w programie Visual Studio, można go zmodyfikować przy użyciu interfejsu użytkownika programu Word. Możesz również użyć dokumentu jako powierzchni projektowej, który umożliwia przeciąganie kontrolek na dział IT. Aby uzyskać więcej informacji, zobacz [projekty pakietu Office w środowisku programu Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="bind-controls-to-data"></a>Powiązywanie kontrolek z danymi
 Formanty zawartości i <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki znajdują się na liście kontrolek, które można przeciągać z okna **źródła danych** . Dodanie formantów zawartości i zakładek w ten sposób powoduje automatyczne powiązanie ich ze źródłem danych, które zostało skonfigurowane przy użyciu okna. Bez pisania kodu, można wyświetlać dane z baz danych, usług i obiektów firmy. Aby uzyskać więcej informacji, zobacz temat [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Następne kroki
 Aby dowiedzieć się, jak utworzyć dostosowanie na poziomie dokumentu dla programu Word, zobacz [Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). W tym instruktażu przedstawiono narzędzia programistyczne pakietu Office w programie Visual Studio oraz model programowania dla dostosowań na poziomie dokumentu programu Word.

 Listę tematów, które przeprowadzą Cię przez niektóre typowe zadania w projektach programu Word, można znaleźć [w temacie typowe zadania w programowaniu pakietu Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Rozwiązania programu Word](../vsto/word-solutions.md)
- [Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
- [Wskazówki dotyczące korzystania z programu Word](../vsto/walkthroughs-using-word.md)
- [Model obiektów programu Word — omówienie](../vsto/word-object-model-overview.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
