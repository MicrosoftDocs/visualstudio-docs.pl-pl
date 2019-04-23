---
title: 'Instrukcje: Wprowadzenie do dostosowywania wstążki'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, adding Ribbon to project
- Ribbon [Office development in Visual Studio], adding
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, adding Ribbon to project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f164a8f1d1c84725530e7a3afab5e63472ae257e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60081570"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Instrukcje: Wprowadzenie do dostosowywania wstążki
  Aby dostosować Wstążki aplikacji pakietu Microsoft Office, należy dodać **Wstążka (Projektant graficzny)** lub **wstążki (XML)** elementu do projektu programu pakietu Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Aby dodać wstążki do projektu

1. Na **projektu** Menu, kliknij przycisk **Dodaj nowy element**.

2. W **Dodaj nowy element** okno dialogowe, wybierz opcję **Wstążka (Projektant graficzny)** lub **wstążki (XML)**. Aby uzyskać więcej informacji na temat tych szablonów, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).

3. W **nazwa** wpisz nazwę elementu wstążki.

    Nazwy nie mogą zawierać następujących znaków:

   - Krzyżyk (#)

   - Procentu (%)

   - Handlowe "i" (&)

   - Gwiazdka (*)

   - Kreski pionowej (|)

   - Ukośnik odwrotny (\\)

   - Dwukropek (:)

   - Podwójny cudzysłów (")

   - Mniej niż (\<)

   - Większe niż (>)

   - Znak zapytania (?)

   - Do przodu ukośnika (/)

   - Spacji wiodących albo końcowych ("")

   - Nazwy zarezerwowane dla Windows lub systemu DOS, np. ("nul", "aux", "con", "com1", "lpt1" i tak dalej)

4. Kliknij przycisk **OK**.

   Element wstążki, który pojawia się w **Eksploratora rozwiązań**. Aby uzyskać informacje o następnych krokach, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).

## <a name="see-also"></a>Zobacz także
- [Dostęp do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [XML — wstążka](../vsto/ribbon-xml.md)
- [Przewodnik: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Przewodnik: Tworzenie kart niestandardowych za pomocą XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
