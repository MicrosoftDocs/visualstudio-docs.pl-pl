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
ms.openlocfilehash: f0b3c6a8a9292ceda03c9d0020b78d9518ca49d9
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252033"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Instrukcje: Przewijanie rekordów bazy danych w arkuszu
  Poniższa procedura pokazuje, jak używać projektanta do wyświetlania jednego pola z tabeli bazy danych w Microsoft Office arkuszu programu Excel z kontrolkami, które umożliwiają użytkownikowi końcowemu przewinięcie wszystkich rekordów.

 Projektanta można używać tylko w projektach na poziomie dokumentu. Można jednak również dodać kontrolki i powiązać je z danymi programowo w czasie wykonywania. Aby uzyskać więcej informacji, [zobacz Przewodnik: Proste powiązanie danych w projekcie](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)dodatku VSTO.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Aby przewijać rekordy bazy danych w arkuszu

1. Otwórz projekt aplikacji programu Excel w programie Visual Studio.

2. Otwórz okno **źródła danych** i Utwórz źródło danych z bazy danych. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych połączeń](../data-tools/add-new-connections.md).

3. Rozwiń tabelę zawierającą dane, które chcesz wyświetlić, a następnie wybierz konkretną kolumnę.

4. Otwórz listę kontrolek i wybierz pozycję **NamedRange**.

5. <xref:Microsoft.Office.Tools.Excel.NamedRange> Przeciągnij kontrolkę na komórkę, w której mają być wyświetlane dane.

6. Na karcie **Windows Forms** **przybornika**Dodaj <xref:System.Windows.Forms.BindingNavigator> kontrolkę do arkusza i skonfiguruj kontrolki, których chcesz użyć. Aby uzyskać więcej informacji, zobacz [BindingNavigator Control &#40;—&#41;Omówienie Windows Forms](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Zobacz także
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
