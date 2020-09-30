---
title: 'Excel: wprowadzenie Programowanie dostosowań na poziomie dokumentu'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cb3b27a4020e2b8947ca0868bb46b5945b5d89de
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585683"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Excel
  Jeśli dopiero zaczynasz tworzyć dostosowania na poziomie dokumentu dla programu Microsoft Office Excel przy użyciu programu Visual Studio, Oto co należy wiedzieć.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-excel-work"></a>Dowiedz się, jak dostosowania na poziomie dokumentu dla programu Excel
 Dostosowanie na poziomie dokumentu dla programu Excel jest oparte na jednym skoroszycie. Aby rozpocząć korzystanie z dostosowania, użytkownik końcowy otwiera skoroszyt lub tworzy skoroszyt z szablonu programu Excel. Zdarzenia w skoroszycie, na przykład wpisywanie w komórkach lub klikanie przycisków i elementów menu, mogą wywołać metody obsługi zdarzeń w zestawie. Gdy skoroszyt zostanie zamknięty, funkcje udostępniane przez dostosowanie nie będą już dostępne w programie Excel, tylko w dokumencie, który je zawiera.

 Aby uzyskać więcej informacji, zobacz [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-excel"></a>Tworzenie projektów na poziomie dokumentu dla programu Excel
 Aby utworzyć dostosowanie na poziomie dokumentu dla programu Excel, użyj szablonu skoroszyt programu Excel lub szablon projektu programu Excel w oknie dialogowym **Nowy projekt** . Szablony te zawierają wymagane odwołania do zestawów i pliki projektu.

 Aby uzyskać więcej informacji na temat tworzenia projektu na poziomie dokumentu dla programu Excel, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Aby uzyskać więcej informacji o szablonach projektów, zobacz [Office Project Templates Overview](../vsto/office-project-templates-overview.md).

## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Programowe skoroszyty programu Excel przy użyciu elementów hosta i kontrolek hosta
 *Elementy hosta* i *formanty hosta* są klasami, które udostępniają model programowania dla dostosowań na poziomie dokumentu utworzonych przy użyciu programu Visual Studio.

 Elementy hosta zapewniają punkt wejścia dla kodu i mogą działać jako kontenery dla formantów hosta i formantów Windows Forms. W projektach na poziomie dokumentu dla programu Excel te elementy hosta są reprezentowane przez `ThisWorkbook` klasy, `Sheet1` , `Sheet2` i `Sheet3` .

 Formanty hosta są oparte na natywnych obiektach programu Excel, takich jak obiekty list i zakresy. Formanty hosta zapewniają podobną funkcjonalność do natywnych obiektów programu Excel, ale mają także nowe zdarzenia, obsługę projektanta i możliwość tworzenia powiązań danych. Są one wyświetlane jako obiekty pierwszej klasy w kodzie projektu i w technologii IntelliSense, które ułatwiają odwoływanie się do określonych obiektów bezpośrednio w kodzie bez konieczności nawigowania po modelu obiektów programu Excel.

 Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)

- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)

- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-excel"></a>Dostosowywanie interfejsu użytkownika programu Excel
 Większość Microsoft Officeych rozwiązań modyfikuje interfejs użytkownika aplikacji pakietu Office, aby zapewnić użytkownikom możliwość współdziałania z rozwiązaniem. Istnieje wiele sposobów modyfikowania interfejsu użytkownika programu Excel przy użyciu dostosowania na poziomie dokumentu. Na przykład można dodać kontrolki do wstążki lub wyświetlić okienko akcji. Aby uzyskać więcej informacji, zobacz temat [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

 Możesz również otworzyć skoroszyt skojarzony z projektem bezpośrednio w programie Visual Studio. Gdy skoroszyt jest otwarty w programie Visual Studio, można zmodyfikować skoroszyt za pomocą interfejsu użytkownika programu Excel. Możesz również użyć skoroszytu jako powierzchni projektowej, co umożliwia przeciąganie kontrolek do arkuszy. Aby uzyskać więcej informacji, zobacz [projekty pakietu Office w środowisku programu Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="use-data-binding"></a>Używanie powiązania danych
 Formanty hosta znajdują się również na liście kontrolek, którą można przeciągnąć z okna **źródła danych** . Dodanie kontrolek hosta w ten sposób powoduje automatyczne powiązanie ich ze źródłem danych, które zostało skonfigurowane przy użyciu okna. Bez pisania kodu, można wyświetlać dane z baz danych, usług sieci Web i obiektów firmowych. Aby uzyskać więcej informacji, zobacz temat [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Następne kroki
 Aby dowiedzieć się, jak utworzyć dostosowanie na poziomie dokumentu dla programu Excel, zobacz [Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). W tym instruktażu przedstawiono narzędzia programistyczne pakietu Office w programie Visual Studio oraz model programowania dla dostosowań na poziomie dokumentu programu Excel.

 Aby zapoznać się z listą tematów, które przeprowadzą Cię przez niektóre typowe zadania w projektach programu Excel, zobacz [typowe zadania w programowaniu pakietu Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Rozwiązania programu Excel](../vsto/excel-solutions.md)
- [Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Wskazówki dotyczące korzystania z programu Excel](../vsto/walkthroughs-using-excel.md)
- [Model obiektów programu Excel — Omówienie](../vsto/excel-object-model-overview.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
