---
title: 'Instrukcje: zapełnianie dokumentów danymi z usług'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 01e2a83f464576d1ca780daa17c0d9478f0caa14
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547150"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Instrukcje: zapełnianie dokumentów danymi z usług

Dostęp do danych działa w taki sam sposób w projektach na poziomie dokumentu dla Microsoft Office, jak w projektach Windows Forms. Używasz tych samych narzędzi i kodu do przenoszenia danych do rozwiązania i możesz nawet użyć formantów Windows Forms, aby wyświetlić dane. Ponadto można korzystać z formantów nazywanych kontrolkami hosta, które są obiektami natywnymi w Microsoft Office Excel i Microsoft Office Word, które zostały ulepszone przy użyciu funkcji zdarzenia i powiązania danych. Aby uzyskać więcej informacji, zobacz [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

Poniższy przykład pokazuje, jak dodać formanty powiązane z danymi do dokumentów w czasie projektowania. Aby zapoznać się z przykładem dodawania formantów związanych z danymi w dodatkach VSTO w czasie wykonywania, zobacz [Przewodnik: powiązanie z danymi z usługi w projekcie dodatku VSTO](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Aby wypełnić projekt na poziomie dokumentu danymi z usługi sieci Web

1. Otwórz okno **źródła danych** i Utwórz źródło danych usługi dla projektu. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md).

2. Przeciągnij żądaną tabelę lub pole z okna **źródła danych** do dokumentu.

     W dokumencie jest tworzony formant, <xref:System.Windows.Forms.BindingSource> który jest powiązany z klasą obiektów w projekcie, a klasy są generowane dla usługi.

3. W kodzie Utwórz wystąpienie klasy usługi sieci Web, z którą nawiązano połączenie w kroku 1.

4. Jeśli istnieją właściwości, które są wymagane do komunikacji z usługą sieci Web, Utwórz wystąpienia tych właściwości.

5. Utwórz i Wyślij żądanie danych przy użyciu metod udostępnianych przez usługę sieci Web i wszystkie wystąpienia właściwości utworzone w kroku 4.

     Używane metody zależą od tego, co oferuje usługa sieci Web.

6. Przypisz odpowiedź danych z usługi sieci Web do <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwości <xref:System.Windows.Forms.BindingSource> .

Po uruchomieniu projektu kontrolki wyświetlają pierwszy rekord w źródle danych. Możesz włączyć przewijanie rekordów przez obsługę zdarzeń walutowych przy użyciu obiektów w <xref:System.Windows.Forms.BindingSource> .

## <a name="see-also"></a>Zobacz także

- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Instrukcje: zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Instrukcje: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Instrukcje: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Instrukcje: aktualizowanie źródła danych przy użyciu danych z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)