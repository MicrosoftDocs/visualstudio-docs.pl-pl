---
title: 'Instrukcje: Zapełnianie dokumentów danymi z usług'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: fe69a35fb7f11eb649a45cd2d2238d1fb8e17ad1
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647039"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Instrukcje: Zapełnianie dokumentów danymi z usług

Dostęp do danych działa tak samo w projektach na poziomie dokumentu, pakietu Microsoft Office, co w projektach Windows Forms. Użyj tego samego narzędzia i kod do przenoszenia danych do rozwiązania i kontrolek formularzy Windows Forms nawet służy do wyświetlania danych. Ponadto możesz korzystać z zalet kontrolki o nazwie formanty hosta, które są natywne obiekty Microsoft Office Excel i Microsoft Office Word, które zostały rozszerzone ze zdarzeniami i możliwość powiązania danych. Aby uzyskać więcej informacji, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

Poniższy przykład pokazuje, jak dodać formanty powiązane z danymi do dokumentów w czasie projektowania. Na przykład sposobu dodawania formantów powiązanych z danymi w dodatkach VSTO w czasie wykonywania zobacz [instruktażu: Powiąż z danymi z usług w projektach dodatku narzędzi VSTO](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).

![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Współdziałanie z usługami sieci web z programu Microsoft Excel? ](http://go.microsoft.com/fwlink/?LinkID=130284).

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Aby wypełnić projektów dokumentów przy użyciu danych z usługi sieci web

1.  Otwórz **źródeł danych** okna i Utwórz źródło danych usługi dla Twojego projektu. Aby uzyskać więcej informacji, zobacz [dodasz nowe źródła danych](../data-tools/add-new-data-sources.md).

2.  Przeciągnij tabelę lub pole, które ma z **źródeł danych** okna dokumentu.

     Kontrolki jest tworzona w dokumencie, <xref:System.Windows.Forms.BindingSource> jest tworzona, jest powiązany z klasy obiektu w projekcie, a klasy są generowane dla usługi.

3.  W kodzie Utwórz wystąpienie klasy usługi sieci web, którą połączenia w kroku 1.

4.  Jeśli istnieją właściwości, które są wymagane do komunikacji z usługą sieci web, tworzenia wystąpień tych właściwości.

5.  Utwórz i Wyślij żądanie danych przy użyciu metod udostępnianych przez usługę sieci Web i wszystkie wystąpienia właściwości utworzonego w kroku 4.

     Metody, których można użyć, zależą od tego, jakie usługi sieci web oferuje.

6.  Przypisz odpowiedzi danych z usługi sieci web do <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwość <xref:System.Windows.Forms.BindingSource>.

Kiedy uruchamiasz projekt, formanty wyświetlania pierwszego rekordu w źródle danych. Możesz włączyć przewijanie rekordów dzięki obsłudze zdarzeń walut, przy użyciu obiektów w <xref:System.Windows.Forms.BindingSource>.

## <a name="see-also"></a>Zobacz także

- [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Instrukcje: Zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Instrukcje: Zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Instrukcje: Zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Instrukcje: Aktualizowanie źródła danych danymi z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)