---
title: 'Instrukcje: zapełnianie arkuszy danymi z bazy danych'
description: Dowiedz się, jak można użyć danych z obiektu w rozwiązaniu oraz jak można użyć formantów Windows Forms, aby wyświetlić dane w arkuszu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 4252eac32540ac2d0b6e763b5b6e9cf0e2ac7055
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846444"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Instrukcje: zapełnianie arkuszy danymi z bazy danych

Dostęp do danych można uzyskać w projektach pakietu Office na poziomie dokumentu w taki sam sposób, jak dostęp do danych w projektach Windows Forms. Używasz tych samych narzędzi i kodu do przenoszenia danych do rozwiązania i możesz nawet użyć formantów Windows Forms, aby wyświetlić dane. Ponadto można korzystać z formantów nazywanych kontrolkami hosta, które są obiektami natywnymi w programie Microsoft Office Excel, które zostały ulepszone przy użyciu funkcji zdarzeń i powiązania danych. Aby uzyskać więcej informacji, zobacz [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

Poniższy przykład pokazuje, jak dodać formanty powiązane z danymi w projektach na poziomie dokumentu przy użyciu projektanta. Aby zapoznać się z przykładem dodawania formantów związanych z danymi w projektach na poziomie aplikacji w czasie wykonywania, zobacz [Przewodnik: złożone powiązanie danych w projekcie dodatku VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>Dodawanie formantu powiązanego z danymi do arkusza w czasie projektowania

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Aby wypełnić arkusz danymi z bazy danych

1. Otwórz projekt na poziomie dokumentu programu Excel w programie Visual Studio, gdy arkusz jest otwarty w projektancie.

2. Otwórz okno **źródła danych** i Utwórz źródło danych dla projektu. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych połączeń](../data-tools/add-new-connections.md).

3. Przeciągnij odpowiednie pole lub tabelę z okna **źródła danych** do arkusza.

Jeden z następujących kontrolek jest tworzony w arkuszu:

- Jeśli przeciągniesz pole, <xref:Microsoft.Office.Tools.Excel.NamedRange> w arkuszu zostanie utworzony formant. Aby uzyskać więcej informacji, zobacz [NamedRange Control](../vsto/namedrange-control.md).

- Jeśli przeciągniesz tabelę, <xref:Microsoft.Office.Tools.Excel.ListObject> w arkuszu zostanie utworzony formant. Aby uzyskać więcej informacji, zobacz [formant ListObject](../vsto/listobject-control.md).

Możesz dodać inny formant, wybierając tabelę lub pole w oknie **źródła danych** , a następnie wybierając inną kontrolkę z listy rozwijanej.

## <a name="objects-in-the-project"></a>Obiekty w projekcie

Oprócz kontrolki następujące obiekty powiązane z danymi są automatycznie dodawane do projektu:

- Typ zestawu danych, który hermetyzuje tabele danych, z którymi nawiązano połączenie w bazie danych. Aby uzyskać więcej informacji, zobacz [Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- A <xref:System.Windows.Forms.BindingSource> , który łączy formant z określonym zestawem danych. Aby uzyskać więcej informacji, zobacz [źródło BindingSource — Omówienie](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- TableAdapter, który nawiązuje połączenie określonego zestawu danych z bazą danych. Aby uzyskać więcej informacji, zobacz [TableAdapter Overview (przegląd](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)).

- TableAdapterManager, który służy do koordynowania kart tabeli w zestawie danych, aby włączyć hierarchiczne aktualizacje. Aby uzyskać więcej informacji, zobacz [hierarchiczne](../data-tools/hierarchical-update.md) informacje o aktualizacji i [TableAdapterManager](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Po uruchomieniu projektu, formant Wyświetla pierwszy rekord w źródle danych. Możesz użyć, <xref:System.Windows.Forms.BindingSource> Aby umożliwić użytkownikom przewijanie rekordów.

### <a name="to-scroll-through-the-records"></a>Aby przewijać rekordy

- Użyj <xref:System.Windows.Forms.BindingSource> metod, takich jak <xref:System.Windows.Forms.BindingSource.MoveNext%2A> i <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> .

Informacje o sposobach wysyłania aktualizacji do określonego zestawu danych i bazy danych znajdują się w temacie [How to: Update a Data Source with Data from a host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Zobacz także

- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Instrukcje: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Instrukcje: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Instrukcje: zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Instrukcje: aktualizowanie źródła danych przy użyciu danych z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)