---
title: 'Instrukcje: Eksportowanie wstążki z projektanta wstążki do XML wstążki'
description: Dowiedz się, że aby dostosować Wstążkę, możesz wyeksportować Wstążkę z projektanta do kodu XML wstążki i bezpośrednio edytować kod XML.
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
ms.openlocfilehash: 2a0511fd103345859f96b18f333465106505057a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953984"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Instrukcje: Eksportowanie wstążki z projektanta wstążki do XML wstążki
  Element **wstążki (projektant graficzny)** nie obsługuje wszystkich możliwych typów dostosowań Wstążki. Aby dostosować Wstążkę w zaawansowanych sposobach, można wyeksportować Wstążkę z projektanta do kodu XML wstążki i bezpośrednio edytować plik XML.

> [!NOTE]
> Nie wszystkie wartości właściwości są wyświetlane w pliku XML wstążki. Aby uzyskać więcej informacji, zobacz [Omówienie wstążki](../vsto/ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Aby wyeksportować Wstążkę z projektanta wstążki do kodu XML wstążki

1. Kliknij prawym przyciskiem myszy plik kodu wstążki w **Eksplorator rozwiązań**, a następnie kliknij pozycję **Projektant widoków**.

2. Kliknij prawym przyciskiem myszy projektanta wstążki, a następnie kliknij polecenie **Eksportuj Wstążkę do formatu XML**.

     Program Visual Studio dodaje plik XML wstążki i plik kodu XML wstążki do projektu.

3. W klasie kodu wstążki Znajdź komentarze, które zaczynają się od `TODO:` .

4. Skopiuj blok kodu z tych komentarzy do klasy **ThisAddIn**, **ThisWorkbook** lub **ThisDocument** , w zależności od typu rozwiązania, które tworzysz.

     Ten kod umożliwia aplikacji Microsoft Office odnajdywanie i ładowanie Wstążki niestandardowej. Aby uzyskać więcej informacji, zobacz [kod XML wstążki](../vsto/ribbon-xml.md).

5. W klasie **ThisAddIn**, **ThisWorkbook** lub **ThisDocument** Usuń komentarz z bloku kodu.

     Po usunięciu komentarza do kodu powinien on wyglądać podobnie do poniższego przykładu. W tym przykładzie Klasa wstążki jest wywoływana `MyRibbon` .

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. Przejdź do pliku kodu XML wstążki i Znajdź `Ribbon Callbacks` region.

     Jest to miejsce, w którym można pisać metody wywołania zwrotnego w celu obsługi akcji użytkownika, takich jak kliknięcie przycisku.

7. Utwórz metodę wywołania zwrotnego dla każdego programu obsługi zdarzeń, który został napisany w kodzie projektanta wstążki.

8. Przenieś cały kod procedury obsługi zdarzeń z obsługi zdarzeń do metod wywołania zwrotnego i zmodyfikuj kod, aby działał z modelem programowania rozszerzalności wstążki (RibbonX).

     Aby uzyskać informacje na temat pisania metod wywołania zwrotnego i korzystania z modelu programowania RibbonX, zobacz [kod XML wstążki](../vsto/ribbon-xml.md).

## <a name="see-also"></a>Zobacz też
- [Omówienie wstążki](../vsto/ribbon-overview.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [XML — Wstążka](../vsto/ribbon-xml.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu języka XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
