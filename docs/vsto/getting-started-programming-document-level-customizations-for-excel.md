---
title: Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Excel
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 808b463445934ecf5cc973b571b4b64d181eb692
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53646948"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Excel
  Jeśli możesz po prostu zaczynasz, tworzenia dostosowań poziomie dokumentu dla programu Microsoft Office Excel przy użyciu programu Visual Studio, Oto, co musisz wiedzieć.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="understand-how-document-level-customizations-for-excel-work"></a>Zrozumienie dostosowań na poziomie dokumentów dla pracy w programie Excel  
 Dostosowania poziomu dokumentu dla programu Excel opiera się wokół pojedynczego skoroszytu. Aby rozpocząć korzystanie z dostosowywania, użytkownik końcowy otwiera skoroszyt lub tworzy skoroszytu na podstawie szablonu programu Excel. Zdarzenia w skoroszycie, na przykład wpisywanie w komórkach lub klikając przyciski i menu, można wywołać metody obsługi zdarzeń w zestawie. Po zamknięciu skoroszytu funkcji oferowanych przez dostosowanie nie są już dostępne w programie Excel, tylko w dokumencie, który je zawiera.  
  
 Aby uzyskać więcej informacji, zobacz [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="create-document-level-projects-for-excel"></a>Tworzenie projektów na poziomie dokumentu dla programu Excel  
 Aby utworzyć dostosowywania poziomie dokumentu dla programu Excel, należy użyć szablonu projektu skoroszyt programu Excel lub szablon programu Excel w **nowy projekt** okno dialogowe. Te szablony zawierają odwołania do zestawów wymagane, a pliki projektu.  
  
 Aby uzyskać więcej informacji o sposobie tworzenia projektu na poziomie dokumentu dla programu Excel, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Aby uzyskać więcej informacji na temat szablonów projektu, zobacz [Przegląd szablony projektu pakietu Office](../vsto/office-project-templates-overview.md).  
  
## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Program skoroszytów programu Excel przy użyciu elementów hosta i kontrolek hosta  
 *Hostowanie elementów* i *hostowania kontrolek* są klasami, które zapewniają model programowania dostosowywania poziomie dokumentu, utworzony przy użyciu programu Visual Studio.  
  
 Obiekty hosta zapewnia punkt wejścia dla kodu i mogą również działać jako kontenery dla formantów hosta i kontrolek formularzy Windows Forms. W projektach na poziomie dokumentu dla programu Excel tych elementów hosta są reprezentowane przez `ThisWorkbook`, `Sheet1`, `Sheet2`, i `Sheet3` klasy.  
  
 Formanty hosta są oparte na natywnych obiektów programu Excel, takich jak lista obiektów i zakresów. Formanty hosta zapewnia funkcje podobne do natywnych obiektów programu Excel, ale mają również nowe zdarzenia, wsparcie oraz możliwość powiązania danych. Pojawiają się jako obiekty najwyższej jakości kodu projektu i technologii IntelliSense, która sprawia, że łatwiej odwoływać się do konkretnych obiektów bezpośrednio w kodzie, bez konieczności przechodzenia z modelu obiektów programu Excel.  
  
 Więcej informacji znajduje się w następujących tematach:  
  
-   [Program dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)  
  
-   [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customize-the-user-interface-of-excel"></a>Dostosowywanie interfejsu użytkownika programu Excel  
 Większość rozwiązań programu Microsoft Office zmodyfikować interfejsu użytkownika (UI) w aplikacji pakietu Office, aby niektóre umożliwiają użytkownikom na interakcję z rozwiązaniem. Istnieje wiele sposobów, w których można zmodyfikować interfejsu użytkownika programu Microsoft Excel za pomocą dostosowania poziomu dokumentu. Na przykład można dodać formanty do Wstążki lub można wyświetlić w okienku Akcje. Aby uzyskać więcej informacji, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
 Możesz również otworzyć skoroszytu, który jest skojarzony z projektem bezpośrednio w programie Visual Studio. Jeśli skoroszyt jest otwarty w programie Visual Studio, można zmodyfikować skoroszytu przy użyciu interfejsu użytkownika programu Excel. Umożliwia także skoroszytu jako powierzchni projektowej, co pozwala na przeciągnij formanty na arkuszy. Aby uzyskać więcej informacji, zobacz [projekty pakietu Office w środowisku Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="use-data-binding"></a>Użyj powiązania danych  
 Formanty hosta są również na liście elementów sterujących, które można przeciągać z **źródeł danych** okna. Dodawanie kontrolki hosta w tym sposób automatycznie wiąże ich źródła danych, które można skonfigurować przy użyciu okna. Bez pisania żadnego kodu, możesz wyświetlić dane z bazy danych, usług sieci web i business obiektów. Aby uzyskać więcej informacji, zobacz [wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Następne kroki  
 Aby dowiedzieć się, jak utworzyć dostosowywania poziomie dokumentu dla programu Excel, zobacz [instruktażu: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). Ten przewodnik stanowi wprowadzenie do narzędzi programistycznych pakietu Office w Visual Studio i modelu programowania dostosowań na poziomie dokumentu programu Excel.  
  
 Aby uzyskać listę tematów, które prowadzą użytkownika przez niektóre typowe zadania w projektach programu Excel, zobacz [typowe zadania w programowaniu Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Program dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)   
 [Rozwiązania programu Excel](../vsto/excel-solutions.md)   
 [Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Wskazówki dotyczące za pomocą programu Excel](../vsto/walkthroughs-using-excel.md)   
 [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md)   
 [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)  
  
  