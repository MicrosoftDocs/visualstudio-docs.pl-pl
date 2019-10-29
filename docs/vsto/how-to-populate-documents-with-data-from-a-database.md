---
title: 'Instrukcje: zapełnianie dokumentów danymi z bazy danych'
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
ms.openlocfilehash: 907b3deeadd0a56f9e47a6e17a40579a0c9ffa64
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985884"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Instrukcje: zapełnianie dokumentów danymi z bazy danych

Można uzyskać dostęp do danych w projektach na poziomie dokumentu dla Microsoft Office w taki sam sposób, w jaki dane są uzyskiwane w projektach Windows Forms. Używasz tych samych narzędzi i kodu do przenoszenia danych z bazy danych do rozwiązania i możesz użyć kontrolek Windows Forms, aby wyświetlić dane.

Ponadto można wyświetlać dane przy użyciu kontrolek hosta. Formanty hosta są obiektami natywnymi w Microsoft Office Word, które zostały ulepszone z możliwością zdarzeń i powiązania danych. Aby uzyskać więcej informacji, zobacz [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

Poniższy przykład pokazuje, jak dodać formanty powiązane z danymi w projektach na poziomie dokumentu przy użyciu projektanta. Aby zapoznać się z przykładem dodawania formantów związanych z danymi w projektach dodatku VSTO w czasie wykonywania, zobacz [Przewodnik: proste powiązanie danych w projekcie dodatku VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

![link do wideo](../vsto/media/playvideo.gif "link do wideo") Aby zapoznać się z pokrewną prezentacją wideo, zobacz temat [Powiązywanie danych z kontrolkami zawartości programu Word 2007 przy użyciu Visual Studio Tools dla systemu Office (3,0)](/previous-versions/office/developer/office-2007/bb967663(v=office.12)).

## <a name="add-a-control-to-a-document-at-design-time"></a>Dodawanie kontrolki do dokumentu w czasie projektowania

### <a name="to-populate-a-document-with-data-from-a-database"></a>Aby wypełnić dokument danymi z bazy danych

1. Otwórz projekt na poziomie dokumentu programu Word w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], gdy dokument zostanie otwarty w projektancie.

2. Otwórz okno **źródła danych** i Utwórz źródło danych z bazy danych. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych połączeń](../data-tools/add-new-connections.md).

3. Przeciągnij odpowiednie pole z okna **źródła danych** do dokumentu.

Kontrolka zawartości zostanie dodana do dokumentu. Typ formantu zawartości zależy od typu danych wybranego pola. Aby uzyskać więcej informacji, zobacz [formanty zawartości](../vsto/content-controls.md).

Możesz dodać inny formant, zaznaczając pole danych w oknie **źródła danych** , a następnie wybierając inną kontrolkę z listy rozwijanej.

## <a name="objects-in-the-project"></a>Obiekty w projekcie

Oprócz kontrolki następujące obiekty powiązane z danymi są automatycznie dodawane do projektu:

- Typ zestawu danych, który hermetyzuje tabele danych, z którymi nawiązano połączenie w bazie danych. Aby uzyskać więcej informacji, zobacz [Narzędzia zestawu danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- <xref:System.Windows.Forms.BindingSource>, który łączy formant z określonym zestawem danych. Aby uzyskać więcej informacji, zobacz [źródło BindingSource — Omówienie](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- TableAdapter, który nawiązuje połączenie określonego zestawu danych z bazą danych. Aby uzyskać więcej informacji, zobacz [Tworzenie i Konfigurowanie TableAdapters](../data-tools/create-and-configure-tableadapters.md).

- TableAdapterManager, który służy do koordynowania kart tabeli w zestawie danych, aby włączyć hierarchiczne aktualizacje. Aby uzyskać więcej informacji, zobacz [hierarchiczne](../data-tools/hierarchical-update.md) informacje o aktualizacji i [TableAdapterManager](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Po uruchomieniu projektu, formant Wyświetla pierwszy rekord w źródle danych. Możesz użyć <xref:System.Windows.Forms.BindingSource>, aby umożliwić użytkownikom przewijanie rekordów.

### <a name="to-scroll-through-the-records"></a>Aby przewijać rekordy

- Użyj metod <xref:System.Windows.Forms.BindingSource>, takich jak <xref:System.Windows.Forms.BindingSource.MoveNext%2A> i <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.

Informacje o sposobach wysyłania aktualizacji do określonego zestawu danych i bazy danych znajdują się w temacie [How to: Update a Data Source with Data from a host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Zobacz także

- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Instrukcje: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Instrukcje: aktualizowanie źródła danych przy użyciu danych z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Korzystanie z plików lokalnej bazy danych w rozwiązaniach pakietu Office — omówienie](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource, składnik — Omówienie](/dotnet/framework/winforms/controls/bindingsource-component-overview)