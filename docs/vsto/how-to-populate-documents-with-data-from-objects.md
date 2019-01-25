---
title: 'Instrukcje: Zapełnianie dokumentów danymi z obiektów'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 571c010aa8b9cda1002a152ed2d528e22b1aa57e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865791"
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Instrukcje: Zapełnianie dokumentów danymi z obiektów

Dane w celu dostępu w obiekcie danych działa tak samo w projektach na poziomie dokumentu, dla programu Microsoft Office Word, jak w projektach Windows Forms. Użyj tego samego narzędzia i kod do przenoszenia danych z obiektu do rozwiązania i kontrolek formularzy Windows Forms służy do wyświetlania danych. Ponadto można wyświetlić dane za pomocą kontrolki hosta. Formanty hosta to natywnych obiektów w programie Microsoft Word pakietu Office, które zostały rozszerzone ze zdarzeniami i możliwości wiązania danych. Aby uzyskać więcej informacji, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

Należy wykonać trzy podstawowe kroki, aby wypełnić dokumentu przy użyciu danych z obiektu:

-   Dodawanie formantu do dokumentu, który można powiązać z danymi.

-   Dodaj obiekt danych do dokumentu.

-   Łączyć się z pomocą elementu BindingSource z obiektu danych.

## <a name="to-add-a-data-object"></a>Aby dodać obiekt danych

Aby dodać obiekt danych, otwórz **źródeł danych** okna i Utwórz źródło danych z obiektu. Aby uzyskać więcej informacji, zobacz [dodasz nowe źródła danych](../data-tools/add-new-data-sources.md).

## <a name="connect-the-data-object-to-the-bindingsource"></a>Obiekt danych nawiązać połączenie z pomocą elementu BindingSource

W projektach na poziomie dokumentu możesz dodać kontrolki do dokumentu i powiązać je z danymi w czasie projektowania.

W projektach dodatku narzędzi VSTO tworzenia formantów i powiązać je w czasie wykonywania.

### <a name="document-level-projects"></a>Projektów na poziomie dokumentu

Aby podłączyć obiekt danych do kontrolki BindingSource:

1.  Przeciągnij pole danych z **źródeł danych** okna dokumentu. Powoduje to automatyczne utworzenie kontrolki.

2.  W kodzie należy utworzyć wystąpienie typu obiektu, który został wybrany dla źródła danych.

3.  Przypisz wystąpienie do <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwość <xref:System.Windows.Forms.BindingSource>.

### <a name="application-level-projects"></a>Projektów na poziomie aplikacji

Aby podłączyć obiekt danych do kontrolki BindingSource:

1.  W kodzie należy utworzyć wystąpienie typu obiektu, który jest skojarzony ze źródłem danych.

2.  Utwórz wystąpienie obiektu <xref:System.Windows.Forms.BindingSource>.

3.  Wystąpienie źródła danych, aby przypisać <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwość <xref:System.Windows.Forms.BindingSource>.

4.  Dodaj źródło danych jako wiązanie danych do kontrolki.

## <a name="see-also"></a>Zobacz także

- [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Instrukcje: Zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Instrukcje: Aktualizowanie źródła danych danymi z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [BindingSource, składnik — omówienie](/dotnet/framework/winforms/controls/bindingsource-component-overview)