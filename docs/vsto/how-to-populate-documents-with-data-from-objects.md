---
title: 'Instrukcje: zapełnianie dokumentów danymi z obiektów'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 38461fc30f71a811033ea70bfe560a6492f56e12
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547176"
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Instrukcje: zapełnianie dokumentów danymi z obiektów

Umożliwianie dostępu do danych w obiekcie danych działa tak samo w projektach na poziomie dokumentu dla Microsoft Office Word, jak w projektach Windows Forms. Używasz tych samych narzędzi i kodu do przenoszenia danych z obiektu do rozwiązania i możesz użyć formantów Windows Forms, aby wyświetlić dane. Ponadto można wyświetlać dane przy użyciu kontrolek hosta. Formanty hosta są obiektami natywnymi w Microsoft Office Word, które zostały ulepszone z możliwością zdarzeń i powiązania danych. Aby uzyskać więcej informacji, zobacz [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

Należy wykonać trzy podstawowe kroki, aby wypełnić dokument danymi z obiektu:

- Dodaj kontrolkę do dokumentu, który można powiązać z danymi.

- Dodaj obiekt danych do dokumentu.

- Połącz obiekt danych z parametrem BindingSource.

## <a name="to-add-a-data-object"></a>Aby dodać obiekt danych

Aby dodać obiekt danych, Otwórz okno **źródła danych** i Utwórz źródło danych na podstawie obiektu. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md).

## <a name="connect-the-data-object-to-the-bindingsource"></a>Łączenie obiektu danych z parametrem BindingSource

W projektach na poziomie dokumentu można dodać kontrolki do dokumentu i powiązać je z danymi w czasie projektowania.

W projektach dodatku VSTO można tworzyć kontrolki i wiązać je w czasie wykonywania.

### <a name="document-level-projects"></a>Projekty na poziomie dokumentu

Aby połączyć obiekt danych z parametrem BindingSource:

1. Przeciągnij odpowiednie pole danych z okna **źródła danych** do dokumentu. Spowoduje to automatyczne utworzenie kontrolki.

2. W kodzie Utwórz wystąpienie typu obiektu, który został wybrany dla źródła danych.

3. Przypisz wystąpienie do <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwości <xref:System.Windows.Forms.BindingSource> .

### <a name="application-level-projects"></a>Projekty na poziomie aplikacji

Aby połączyć obiekt danych z parametrem BindingSource:

1. W kodzie Utwórz wystąpienie typu obiektu, który jest skojarzony ze źródłem danych.

2. Utwórz wystąpienie klasy <xref:System.Windows.Forms.BindingSource>.

3. Przypisz wystąpienie źródła danych do <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwości <xref:System.Windows.Forms.BindingSource> .

4. Dodaj źródło danych do kontrolki.

## <a name="see-also"></a>Zobacz też

- [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Instrukcje: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Instrukcje: aktualizowanie źródła danych przy użyciu danych z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [BindingSource, składnik — Omówienie](/dotnet/framework/winforms/controls/bindingsource-component-overview)