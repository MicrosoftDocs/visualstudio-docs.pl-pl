---
title: 'Instrukcje: Zapełnianie dokumentów danymi z bazy danych'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4ec56ae4345405cfc704a97ec624f9c2e4d96a5b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061215"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Instrukcje: Zapełnianie dokumentów danymi z bazy danych

Można uzyskujesz dostęp do danych w projektach na poziomie dokumentu dla programu Microsoft Office w taki sam sposób, uzyskujesz dostęp do danych w projektach Windows Forms. Użyj tego samego narzędzia i kod do przenoszenia danych z bazy danych w rozwiązaniu i kontrolek formularzy Windows Forms służy do wyświetlania danych.

Ponadto można wyświetlić dane za pomocą kontrolki hosta. Formanty hosta to natywnych obiektów w programie Microsoft Word pakietu Office, które zostały rozszerzone ze zdarzeniami i możliwości wiązania danych. Aby uzyskać więcej informacji, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

Poniższy przykład pokazuje, jak dodać formanty powiązane z danymi w użyciu projektanta projektów na poziomie dokumentu. Na przykład sposobu dodawania formantów powiązanych z danymi w projektach dodatku narzędzi VSTO w czasie wykonywania zobacz [instruktażu: Proste powiązanie danych w projekcie dodatku narzędzi VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [powiązywanie danych do programu Word 2007 zawartości kontrolki przy użyciu programu Visual Studio Tools dla pakietu Office (3.0)](http://go.microsoft.com/fwlink/?LinkId=136785).

## <a name="add-a-control-to-a-document-at-design-time"></a>Dodawanie kontrolki do dokumentu w czasie projektowania

### <a name="to-populate-a-document-with-data-from-a-database"></a>Aby wypełnić dokumentu przy użyciu danych z bazy danych

1. Otwórz projekt poziomu dokumentu programu Word w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dokument jest otwarty w projektancie.

2. Otwórz **źródeł danych** okna i Utwórz źródło danych z bazy danych. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).

3. Przeciągnij pole z **źródeł danych** okna dokumentu.

Kontrolki zawartości zostanie dodany do dokumentu. Typ zawartości kontrolki zależy od typu danych pola, które wybrano. Aby uzyskać więcej informacji, zobacz [udostępnia mechanizmy kontroli zawartości](../vsto/content-controls.md).

Innej kontrolki można dodawać przez zaznaczenie pola danych **źródeł danych** okna, a następnie wybierając innej kontrolki z listy rozwijanej.

## <a name="objects-in-the-project"></a>Obiekty w projekcie

Oprócz sterowania następujące obiekty powiązane dane są automatycznie dodawane do projektu:

- Wpisany zestaw danych, który hermetyzuje tabelami danych, które łączysz się w bazie danych. Aby uzyskać więcej informacji, zobacz [narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- A <xref:System.Windows.Forms.BindingSource> który formant łączy się z zestawu danych. Aby uzyskać więcej informacji, zobacz [— informacje o składniku BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- TableAdapter, łączącej typizowany zestaw danych w bazie danych. Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie adapterów TableAdapter](../data-tools/create-and-configure-tableadapters.md).

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
- [Instrukcje: Aktualizowanie źródła danych danymi z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Korzystać z plików lokalnej bazy danych w rozwiązań Office ― omówienie](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource, składnik — omówienie](/dotnet/framework/winforms/controls/bindingsource-component-overview)