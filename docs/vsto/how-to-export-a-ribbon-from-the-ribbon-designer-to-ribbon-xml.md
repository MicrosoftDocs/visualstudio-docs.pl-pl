---
title: 'How to: Export a ribbon from the Ribbon Designer to Ribbon XML'
description: Dowiedz się, że aby dostosować wstążkę, możesz wyeksportować wstążkę z projektanta do pliku XML wstążki i edytować kod XML bezpośrednio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1514410094deaf9c77e088c3b69e2d39d29175c2
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825592"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>How to: Export a ribbon from the Ribbon Designer to Ribbon XML
  Element **Wstążka (Projektant wizualny)** nie obsługuje wszystkich możliwych typów dostosowywania wstążki. Aby dostosować wstążkę w zaawansowany sposób, możesz wyeksportować wstążkę z projektanta do pliku XML wstążki i edytować kod XML bezpośrednio.

> [!NOTE]
> Nie wszystkie wartości właściwości są wyświetlane w pliku XML wstążki. Aby uzyskać więcej informacji, zobacz [Omówienie wstążki](../vsto/ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Aby wyeksportować wstążkę z Projektanta wstążki do pliku XML wstążki

1. Kliknij prawym przyciskiem myszy plik kodu wstążki w **Eksplorator rozwiązań**, a następnie kliknij **Projektant widoków**.

2. Kliknij prawym przyciskiem myszy projektanta wstążki, a następnie kliknij polecenie **Eksportuj wstążkę do pliku XML.**

     Visual Studio dodaje plik XML wstążki i plik kodu XML wstążki do projektu.

3. W klasie Kodu wstążki znajdź komentarze, które zaczynają się od `TODO:` .

4. Skopiuj blok kodu w tych komentarzach do klasy **ThisAddin,** **ThisWorkbook** lub **ThisDocument,** w zależności od typu rozwiązania, które opracowujesz.

     Ten kod umożliwia aplikacji Microsoft Office odnajdywanie i ładowanie niestandardowej wstążki. Aby uzyskać więcej informacji, zobacz [Xml wstążki](../vsto/ribbon-xml.md).

5. W klasie **ThisAddin**, **ThisWorkbook** lub **ThisDocument odkomentuj** blok kodu.

     Po odkodowyniu kodu powinien on wyglądać jak w poniższym przykładzie. W tym przykładzie klasa wstążki nosi nazwę `MyRibbon` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb" id="Snippet1":::

6. Przejdź do pliku kodu XML wstążki i znajdź `Ribbon Callbacks` region.

     W tym miejscu pisze się metody wywołania zwrotnego do obsługi akcji użytkownika, takich jak kliknięcie przycisku.

7. Utwórz metodę wywołania zwrotnego dla każdego programu obsługi zdarzeń, który został napisany w kodzie projektanta wstążki.

8. Przenieś cały kod procedury obsługi zdarzeń z programów obsługi zdarzeń do metod wywołania zwrotnego i zmodyfikuj kod tak, aby działał z modelem programowania rozszerzalności wstążki (RibbonX).

     Aby uzyskać informacje na temat pisania metod wywołania zwrotnego i korzystania z modelu programowania RibbonX, zobacz [Xml wstążki](../vsto/ribbon-xml.md).

## <a name="see-also"></a>Zobacz też
- [Omówienie wstążki](../vsto/ribbon-overview.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [XML — Wstążka](../vsto/ribbon-xml.md)
- [Przewodnik: tworzenie karty niestandardowej przy użyciu Projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Przewodnik: tworzenie karty niestandardowej przy użyciu xml wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
