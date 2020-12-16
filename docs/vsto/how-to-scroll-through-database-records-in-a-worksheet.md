---
title: 'Instrukcje: przewijanie rekordów bazy danych w arkuszu'
description: Dowiedz się, jak za pomocą projektanta wyświetlić jedno pole z tabeli bazy danych w arkuszu programu Microsoft Excel
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 536a3cca0337e8879e64cbc3ffc15b8411c201b6
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528170"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Instrukcje: przewijanie rekordów bazy danych w arkuszu
  Poniższa procedura pokazuje, jak używać projektanta do wyświetlania jednego pola z tabeli bazy danych w Microsoft Office arkuszu programu Excel z kontrolkami, które umożliwiają użytkownikowi końcowemu przewinięcie wszystkich rekordów.

 Projektanta można używać tylko w projektach na poziomie dokumentu. Można jednak również dodać kontrolki i powiązać je z danymi programowo w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Przewodnik: proste powiązanie danych w projekcie dodatku VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Aby przewijać rekordy bazy danych w arkuszu

1. Otwórz projekt aplikacji programu Excel w programie Visual Studio.

2. Otwórz okno **źródła danych** i Utwórz źródło danych z bazy danych. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych połączeń](../data-tools/add-new-connections.md).

3. Rozwiń tabelę zawierającą dane, które chcesz wyświetlić, a następnie wybierz konkretną kolumnę.

4. Otwórz listę kontrolek i wybierz pozycję **NamedRange**.

5. Przeciągnij <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę na komórkę, w której mają być wyświetlane dane.

6. Na karcie **Windows Forms** **przybornika** Dodaj <xref:System.Windows.Forms.BindingNavigator> kontrolkę do arkusza i skonfiguruj kontrolki, których chcesz użyć. Aby uzyskać więcej informacji, zobacz [BindingNavigator Control overview &#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Zobacz też
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
