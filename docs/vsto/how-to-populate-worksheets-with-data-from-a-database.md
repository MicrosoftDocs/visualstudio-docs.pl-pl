---
title: 'Instrukcje: Zapełnianie arkuszy danymi z bazy danych'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 67c12843d00bf8d5af51fa7af3175077527afa58
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967764"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Instrukcje: Zapełnianie arkuszy danymi z bazy danych

W taki sam sposób, uzyskujesz dostęp do danych w projektach formularzy Windows mogą uzyskać dostęp do danych w projektach pakietu Office poziomie dokumentu. Użyj tego samego narzędzia i kod do przenoszenia danych do rozwiązania i kontrolek formularzy Windows Forms nawet służy do wyświetlania danych. Ponadto możesz korzystać z zalet kontrolki o nazwie formanty hosta, które są natywne obiektów w programie Microsoft Office Excel, które zostały rozszerzone ze zdarzeniami i możliwości wiązania danych. Aby uzyskać więcej informacji, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

Poniższy przykład pokazuje, jak dodać formanty powiązane z danymi w użyciu projektanta projektów na poziomie dokumentu. Na przykład sposobu dodawania formantów powiązanych z danymi w projektach na poziomie aplikacji w czasie wykonywania zobacz [instruktażu: Złożone powiązanie danych w projekcie dodatku narzędzi VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).

![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Przesyłanie danych do arkusza programu Excel? ](http://go.microsoft.com/fwlink/?LinkID=130277), i [jak: Używanie bazy danych w programie Excel? ](http://go.microsoft.com/fwlink/?LinkID=130287).

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>Dodaj formant powiązany z danymi do arkusza w czasie projektowania

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Aby wypełnić arkusza z danymi z bazy danych

1. Otwórz projekt poziomu dokumentu programu Excel w programie Visual Studio po otwarciu arkusza w projektancie.

2. Otwórz **źródeł danych** okna i Utwórz źródło danych dla projektu. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).

3. Przeciągnij pole lub tabela, z **źródeł danych** okna do arkusza.

Jedną z następujących formantów jest tworzony w arkuszu:

- Jeśli przeciągniesz pole <xref:Microsoft.Office.Tools.Excel.NamedRange> formant zostanie utworzony w arkuszu. Aby uzyskać więcej informacji, zobacz [kontrolki NamedRange](../vsto/namedrange-control.md).

- Jeśli przeciągniesz tabeli <xref:Microsoft.Office.Tools.Excel.ListObject> formant zostanie utworzony w arkuszu. Aby uzyskać więcej informacji, zobacz [kontrolki ListObject](../vsto/listobject-control.md).

Można dodać innej kontrolki, wybierając tabelę lub pole **źródeł danych** okna, a następnie wybierając innej kontrolki z listy rozwijanej.

## <a name="objects-in-the-project"></a>Obiekty w projekcie

Oprócz sterowania następujące obiekty powiązane dane są automatycznie dodawane do projektu:

- Wpisany zestaw danych, który hermetyzuje tabelami danych, które łączysz się w bazie danych. Aby uzyskać więcej informacji, zobacz [narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- A <xref:System.Windows.Forms.BindingSource> który formant łączy się z zestawu danych. Aby uzyskać więcej informacji, zobacz [— informacje o składniku BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- TableAdapter, łączącej typizowany zestaw danych w bazie danych. Aby uzyskać więcej informacji, zobacz [TableAdapter — Przegląd](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

- TableAdapterManager, który służy do koordynowania adapterów tabel w zestawie danych w celu włączenia aktualizacji hierarchicznej. Aby uzyskać więcej informacji, zobacz [hierarchiczna aktualizacja](../data-tools/hierarchical-update.md) i [odwołania TableAdapterManager](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Kiedy uruchamiasz projekt, kontrolka ma wyświetlać pierwszego rekordu w źródle danych. Możesz użyć <xref:System.Windows.Forms.BindingSource> aby umożliwić użytkownikom do przewijania rekordów.

### <a name="to-scroll-through-the-records"></a>Do przewijania rekordów

- Użyj <xref:System.Windows.Forms.BindingSource> metody takie jak <xref:System.Windows.Forms.BindingSource.MoveNext%2A> i <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Aby uzyskać informacje o sposobie wysyłania aktualizacji do zestawu danych i bazę danych, zobacz [jak: Aktualizowanie źródła danych danymi z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Zobacz także

- [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Instrukcje: Zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Instrukcje: Zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Instrukcje: Zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Instrukcje: Aktualizowanie źródła danych danymi z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Jak mogę Przesyłanie danych do arkusza programu Excel](http://go.microsoft.com/fwlink/?LinkID=130277)
- [Jak mogę Używanie bazy danych w programie Excel?](http://go.microsoft.com/fwlink/?LinkID=130287)