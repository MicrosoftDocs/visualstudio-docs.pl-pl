---
title: 'Instrukcje: wprowadzenie do dostosowywania wstążki'
description: Dowiedz się, że aby dostosować Wstążkę Microsoft Office aplikacji, Dodaj Wstążkę (Visual Designer) lub Wstążkę (XML) do projektu pakietu Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d82d059166b9efbb80ed6ce4cffcbb973235b01b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953919"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Instrukcje: wprowadzenie do dostosowywania wstążki
  Aby dostosować Wstążkę Microsoft Office aplikacji, Dodaj **Wstążkę (Visual Designer)** lub **Wstążkę (XML)** do projektu pakietu Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>Aby dodać Wstążkę do projektu

1. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **wstążka (projektant graficzny)** lub **wstążka (XML)**. Aby uzyskać więcej informacji na temat tych szablonów, zobacz [Omówienie wstążki](../vsto/ribbon-overview.md).

3. W polu **Nazwa** wpisz nazwę elementu wstążki.

    Nazwy nie mogą zawierać następujących znaków:

   - Funt (#)

   - Procent (%)

   - Handlowe "i" (&)

   - Gwiazdka (*)

   - Kreska pionowa (|)

   - Ukośnik odwrotny ( \\ )

   - Dwukropek (:)

   - Podwójny cudzysłów (")

   - Mniejsze niż ( \< )

   - Większe niż (>)

   - Znak zapytania (?)

   - Ukośnik (/)

   - Spacje początkowe lub końcowe ("")

   - Nazwy zarezerwowane dla systemu Windows lub DOS, takie jak ("NUL", "AUX", "con", "COM1", "LPT1" itd.)

4. Kliknij przycisk **OK**.

   Element wstążki zostanie wyświetlony w **Eksplorator rozwiązań**. Aby uzyskać informacje o następnych krokach, zobacz [Omówienie wstążki](../vsto/ribbon-overview.md).

## <a name="see-also"></a>Zobacz też
- [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)
- [Projektant wstążki](../vsto/ribbon-designer.md)
- [XML — Wstążka](../vsto/ribbon-xml.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu języka XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
