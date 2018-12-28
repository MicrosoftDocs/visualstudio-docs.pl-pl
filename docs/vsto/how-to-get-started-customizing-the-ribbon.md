---
title: 'Instrukcje: Wprowadzenie do dostosowywania wstążki'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: e52efc4cfd1252ff908785195df5c06b8bc90baa
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647152"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>Instrukcje: Wprowadzenie do dostosowywania wstążki
  Aby dostosować Wstążki aplikacji pakietu Microsoft Office, należy dodać **Wstążka (Projektant graficzny)** lub **wstążki (XML)** elementu do projektu programu pakietu Office.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-a-ribbon-to-a-project"></a>Aby dodać wstążki do projektu  
  
1. Na **projektu** Menu, kliknij przycisk **Dodaj nowy element**.  
  
2. W **Dodaj nowy element** okno dialogowe, wybierz opcję **Wstążka (Projektant graficzny)** lub **wstążki (XML)**. Aby uzyskać więcej informacji na temat tych szablonów, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).  
  
3. W **nazwa** wpisz nazwę elementu wstążki.  
  
    Nazwy nie mogą zawierać następujących znaków:  
  
   -   Krzyżyk (#)  
  
   -   Procentu (%)  
  
   -   Handlowe "i" (&)  
  
   -   Gwiazdka (*)  
  
   -   Kreski pionowej (|)  
  
   -   Ukośnik odwrotny (\\)  
  
   -   Dwukropek (:)  
  
   -   Podwójny cudzysłów (")  
  
   -   Mniej niż (\<)  
  
   -   Większe niż (>)  
  
   -   Znak zapytania (?)  
  
   -   Do przodu ukośnika (/)  
  
   -   Spacji wiodących albo końcowych ("")  
  
   -   Nazwy zarezerwowane dla Windows lub systemu DOS, np. ("nul", "aux", "con", "com1", "lpt1" i tak dalej)  
  
4. Kliknij przycisk **OK**.  
  
   Element wstążki, który pojawia się w **Eksploratora rozwiązań**. Aby uzyskać informacje o następnych krokach, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Dostęp do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Projektant wstążki](../vsto/ribbon-designer.md)   
 [XML — Wstążka](../vsto/ribbon-xml.md)   
 [Przewodnik: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Przewodnik: Tworzenie kart niestandardowych za pomocą XML wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  