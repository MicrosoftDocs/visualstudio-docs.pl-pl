---
title: 'Instrukcje: Przewijanie rekordów bazy danych w arkuszu'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 47a95db3797592f4c8d55ffa72e0e7323d251378
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863607"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Instrukcje: Przewijanie rekordów bazy danych w arkuszu
  Poniższa procedura pokazuje, jak używać projektanta do wyświetlania jedno pole z tabeli bazy danych w arkuszu programu Microsoft Office Excel, za pomocą formantów, które umożliwiają użytkownikowi końcowemu przewiń wszystkie rekordy.  
  
 Tylko w projektach na poziomie dokumentu można używać projektanta. Można również dodawać formanty i powiązać je z danymi programowo w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [instruktażu: Proste powiązanie danych w projekcie dodatku narzędzi VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Do przewijania rekordów bazy danych w arkuszu  
  
1.  Otwórz projekt aplikacji programu Excel w programie Visual Studio.  
  
2.  Otwórz **źródeł danych** okna i Utwórz źródło danych z bazy danych. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).  
  
3.  Rozwiń tabelę, która zawiera dane, które mają być wyświetlane, a następnie wybierz określone kolumny.  
  
4.  Otwórz listę kontrolek, a następnie wybierz pozycję **NamedRange**.  
  
5.  Przeciągnij <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli na komórkę, w którym ma się pojawić się dane.  
  
6.  Z **Windows Forms** karcie **przybornika**, Dodaj <xref:System.Windows.Forms.BindingNavigator> sterowania do arkusza i konfigurowanie kontrolek, w której chcesz użyć. Aby uzyskać więcej informacji, zobacz [— informacje o formancie BindingNavigator &#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>Zobacz także  
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
