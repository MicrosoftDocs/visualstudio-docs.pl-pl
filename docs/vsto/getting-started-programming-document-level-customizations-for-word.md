---
title: Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word
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
ms.openlocfilehash: 2b2872ca6496444cbb3878dc39800a8661400a76
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056331"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word
  Jeśli możesz po prostu zaczynasz, tworzenia dostosowań poziomie dokumentu dla programu Microsoft Word pakietu Office przy użyciu programu Visual Studio, Oto, co musisz wiedzieć.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-word-work"></a>Zrozumienie dostosowań na poziomie dokumentów dla pracy w programie Word
 Każde dostosowanie programu Word, tworzonych jest na podstawie pojedynczego dokumentu. Aby rozpocząć korzystanie z dostosowywania, użytkownik końcowy otwiera dokument lub tworzy dokumentu z szablonu programu Word. Zdarzenia w dokumencie, na przykład przeniesienie kursora do określonych obszarów lub klikając przyciski i menu, można wywołać metody obsługi zdarzeń w zestawie. Gdy dokument zostanie zamknięty, funkcji oferowanych przez dostosowanie nie są już dostępne w programie Word.

 Aby uzyskać więcej informacji, zobacz [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-word"></a>Tworzenie projektów na poziomie dokumentu dla programu Word
 Aby utworzyć dostosowywania poziomie dokumentu dla programu Word, należy użyć szablonu projektu dokument programu Word lub szablon programu Word w **nowy projekt** okno dialogowe. Te szablony zawierają odwołania do zestawów wymagane, a pliki projektu.

 Aby uzyskać więcej informacji o tym, jak utworzyć projekt na poziomie dokumentu dla programu Word, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Aby uzyskać więcej informacji na temat szablonów projektu, zobacz [Przegląd szablony projektu pakietu Office](../vsto/office-project-templates-overview.md).

## <a name="program-word-documents-by-using-host-items-host-controls"></a>Program dokumentów programu Word za pomocą kontrolki hosta elementów hosta
 *Hostowanie elementów* i *hostowania kontrolek* są klasami, które zapewniają modelu programowania dostosowań na poziomie dokumentu.

 Obiekty hosta zapewnia punkt wejścia dla kodu i mogą również działać jako kontenery dla formantów hosta i kontrolek formularzy Windows Forms. W projektach na poziomie dokumentu dla programu Word element hosta jest reprezentowany przez `ThisDocument` klasy.

 Formanty hosta są oparte na natywnych obiektów programu Word, takie jak formanty zawartości, zakładki i węzłów XML. Formanty hosta zapewnia funkcje podobne do natywnych obiektów programu Word, ale mają również nowe zdarzenia, Obsługa projektanta i możliwości wiązania danych. Pojawiają się jako obiekty najwyższej jakości kodu projektu i technologii IntelliSense, która sprawia, że łatwiej odwoływać się do konkretnych obiektów bezpośrednio w kodzie, bez konieczności przechodzenia z modelu obiektów programu Word.

 Więcej informacji znajduje się w następujących tematach:

- [Program dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)

- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)

- [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-word"></a>Dostosowywanie interfejsu użytkownika programu Word
 Większość rozwiązań programu Microsoft Office zmodyfikować interfejsu użytkownika (UI) w aplikacji pakietu Office, aby niektóre umożliwiają użytkownikom na interakcję z rozwiązaniem. Istnieje wiele sposobów, w których można zmodyfikować interfejsu użytkownika programu Word za pomocą dostosowania poziomu dokumentu. Na przykład można dodać formanty do Wstążki i można wyświetlić w okienku Akcje. Aby uzyskać więcej informacji, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

 Można również otworzyć dokument, który jest skojarzony z projektem bezpośrednio w programie Visual Studio. Gdy dokument jest otwarty w programie Visual Studio, można zmodyfikować dokumentu przy użyciu interfejsu użytkownika programu Word. Umożliwia także dokumentu jako powierzchni projektowej, co pozwala na przeciągnij formanty. Aby uzyskać więcej informacji, zobacz [projekty pakietu Office w środowisku Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="bind-controls-to-data"></a>Powiązywanie kontrolek z danymi
 Formanty zawartości i <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki znajdują się na liście elementów sterujących, które można przeciągać z **źródeł danych** okna. Dodawanie zawartości kontrolki i zakładki w ten sposób automatycznie wiąże je do źródła danych, które można skonfigurować przy użyciu okna. Bez pisania żadnego kodu, możesz wyświetlić dane z bazy danych, usług i obiektów biznesowych. Aby uzyskać więcej informacji, zobacz [wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Następne kroki
 Aby dowiedzieć się, jak utworzyć dostosowywania poziomie dokumentu dla programu Word, zobacz [instruktażu: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). Ten przewodnik stanowi wprowadzenie do narzędzi programistycznych pakietu Office w Visual Studio i modelu programowania dostosowań na poziomie dokumentu programu Word.

 Aby uzyskać listę tematów, które prowadzą użytkownika przez niektóre typowe zadania w projektach programu Word, zobacz [typowe zadania w programowaniu Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)
- [Rozwiązania programu Word](../vsto/word-solutions.md)
- [Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
- [Wskazówki dotyczące przy użyciu programu Word](../vsto/walkthroughs-using-word.md)
- [Model obiektu Word — omówienie](../vsto/word-object-model-overview.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
