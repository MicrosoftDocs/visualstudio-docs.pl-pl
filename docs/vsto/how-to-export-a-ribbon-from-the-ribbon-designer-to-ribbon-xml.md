---
title: 'Instrukcje: Eksportowanie wstążki z projektanta wstążki do XML wstążki'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- Ribbon [Office development in Visual Studio], exporting
- XML [Office development in Visual Studio], Ribbon
- Ribbon Designer [Office development in Visual Studio]
- exporting Ribbon
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 370c2e1d08c47b8a5068d0227426d2b4083590a5
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53646935"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Instrukcje: Eksportowanie wstążki z projektanta wstążki do XML wstążki
  **Wstążka (Projektant graficzny)** element nie obsługuje wszystkich możliwych typów dostosowania wstążki. W celu dostosowania wstążki w zaawansowanych sposobów, możesz eksportowanie wstążki z projektanta do pliku XML Wstążki i bezpośredniego edytowania pliku XML.  
  
> [!NOTE]  
>  Nie wszystkie wartości właściwości są wyświetlane w pliku XML wstążki. Aby uzyskać więcej informacji, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Aby eksportowanie wstążki z projektanta wstążki do XML wstążki  
  
1.  Kliknij prawym przyciskiem myszy plik kodu wstążki w **Eksploratora rozwiązań**, a następnie kliknij przycisk **Projektant widoków**.  
  
2.  Kliknij prawym przyciskiem myszy projektanta wstążki, a następnie kliknij przycisk **eksportowanie wstążki do XML**.  
  
     Visual Studio dodaje pliku XML Wstążki i pliku kodu XML wstążki do projektu.  
  
3.  W klasie kodu wstążki, zlokalizuj komentarzy rozpoczynających się od `TODO:`.  
  
4.  Skopiuj blok kodu w tych komentarzach do **ThisAddin**, **ThisWorkbook**, lub **ThisDocument** klasy, w zależności od tego, jakiego typu rozwiązania tworzenia.  
  
     Ten kod umożliwia aplikacji Microsoft Office wykrycie i załadowanie swoje niestandardowe wstążki. Aby uzyskać więcej informacji, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).  
  
5.  W **ThisAddin**, **ThisWorkbook**, lub **ThisDocument** klasy, Usuń komentarz z bloku kodu.  
  
     Po użytkownik Usuń komentarz kodu, powinien on przypominać następujący przykład. W tym przykładzie jest wywoływana w klasie wstążki `MyRibbon`.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  Przejdź do pliku kodu XML wstążki, a następnie znajdź `Ribbon Callbacks` regionu.  
  
     Jest to, gdzie można wpisać metody wywołania zwrotnego do obsługi akcje użytkownika, takie jak kliknięcie przycisku.  
  
7.  Utwórz metodę wywołania zwrotnego dla każdego programu obsługi zdarzeń, który zapisano w kodzie projektanta wstążki.  
  
8.  Przenieś wszystkie swój kod procedury obsługi zdarzeń z programu obsługi zdarzeń do metod wywołania zwrotnego i zmodyfikuj kod do działania z modelu programowania rozszerzalności wstążki (RibbonX).  
  
     Aby uzyskać informacji na temat pisania metody wywołania zwrotnego i za pomocą modelu programowania RibbonX, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Wstążka — omówienie](../vsto/ribbon-overview.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [XML — Wstążka](../vsto/ribbon-xml.md)   
 [Przewodnik: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Przewodnik: Tworzenie kart niestandardowych za pomocą XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  