---
title: Korzystanie z formantów WPF w rozwiązaniach pakietu Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 717e24315d1f6e57eda224ef17cc4ea5b5d550c9
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189749"
---
# <a name="use-wpf-controls-in-office-solutions"></a>Korzystanie z formantów WPF w rozwiązaniach pakietu Office

Mimo że rozwiązania utworzone przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio są przeznaczone do pracy bezpośrednio z kontrolkami Windows Forms, można również użyć formantów WPF w rozwiązaniach. Windows Presentation Foundation (WPF) jest alternatywą dla Windows Forms projektowania interfejsów użytkownika. WPF używa języka znaczników o nazwie Extensible Application Markup Language (XAML), aby zapewnić nowe techniki do dołączania interfejsu użytkownika, multimediów i dokumentów. Aby uzyskać więcej informacji, zobacz [Omówienie WPF](/dotnet/framework/wpf/introduction-to-wpf).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

Każdy element interfejsu użytkownika, który może hostować Windows Forms formantów w rozwiązaniu pakietu Office, może również hostować formanty WPF. Należą do nich następujące elementy:

- Dokumenty i arkusze w dostosowaniu na poziomie dokumentu.

- Okienka akcji w dostosowaniach na poziomie dokumentu.

- Niestandardowe okienka zadań w dodatkach narzędzi VSTO.

- Regiony formularzy w dodatkach narzędzi VSTO dla programu Outlook.

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>Dodawanie formantów WPF do projektów pakietu Office w czasie projektowania

Nie można dodać formantów WPF bezpośrednio do elementów interfejsu użytkownika w rozwiązaniach pakietu Office. Zamiast tego Dodaj element **kontrolki użytkownika (WPF)** do projektu i użyj go jako powierzchni projektowej dla formantów WPF. Następnie Dodaj kontrolkę użytkownika WPF do elementu interfejsu użytkownika w projekcie.

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Aby dodać formanty WPF do okienka Akcje, niestandardowego okienka zadań lub regionu formularza

1. Otwórz projekt, do którego chcesz dodać niestandardowe okienko zadań, okienko akcji lub region formularza.

2. Dodaj element **kontrolki użytkownika (WPF)** do projektu.

3. Z **przybornika**Dodaj formanty WPF do powierzchni projektu kontrolki użytkownika WPF.

     Domyślnie gdy projektant formantów użytkownika WPF jest otwarty, **Przybornik** zawiera tylko formanty WPF.

4. Skompiluj projekt.

5. Dodawanie okienka akcji, regionu formularza lub niestandardowego okienka zadań do projektu:

    - W przypadku regionów formularzy Dodaj element **regionu formularza programu Outlook** do projektu. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

    - W przypadku okienek akcji Dodaj **kontrolkę okienko akcji** lub element **kontrolki użytkownika** do projektu. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie akcji okienka do dokumentów programu Word lub skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

    - W przypadku niestandardowych okienek zadań Dodaj element **kontrolki użytkownika** do projektu. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

6. Na karcie **formanty użytkownika WPF** ProjectName w **przyborniku**przeciągnij kontrolkę użytkownika WPF do projektanta dla okienka Akcje, regionu formularza lub niestandardowego okienka zadań.

     Program Visual Studio automatycznie tworzy obiekt <xref:System.Windows.Forms.Integration.ElementHost>, który hostuje kontrolkę użytkownika WPF dla elementu interfejsu użytkownika.

7. Ponownie skompiluj projekt.

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Aby dodać formanty WPF do dokumentu lub arkusza w projekcie na poziomie dokumentu

1. Otwórz projekt na poziomie dokumentu dla programu Word lub Excel.

2. Dodaj element **kontrolki użytkownika (WPF)** do projektu.

3. Z **przybornika**Dodaj formanty WPF do powierzchni projektu kontrolki użytkownika WPF.

4. Skompiluj projekt.

5. Dodaj element **kontrolki użytkownika** (czyli Windows Forms kontrolkę użytkownika) do projektu.

6. Otwórz projektanta dla kontrolki użytkownika Windows Forms.

7. Na karcie **formanty użytkownika WPF** ProjectName w **przyborniku**przeciągnij kontrolkę użytkownika WPF do projektanta.

     Program Visual Studio automatycznie tworzy obiekt <xref:System.Windows.Forms.Integration.ElementHost>, który hostuje kontrolkę użytkownika WPF w kontrolce użytkownika Windows Forms.

8. Napisz kod, który programowo dodaje kontrolkę użytkownika Windows Forms do dokumentu lub skoroszytu. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

    > [!NOTE]
    > Nie można przeciągnąć kontrolki użytkownika Windows Forms do dokumentu lub arkusza w projektancie.

9. Ponownie skompiluj projekt.

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>Hostowanie formantów WPF za pomocą klasy ElementHost

Program Visual Studio udostępnia funkcje, które ułatwiają korzystanie z Windows Forms formantów w rozwiązaniach pakietu Office, ale nie udostępniają podobnych funkcji dla formantów WPF. Na przykład można dodać kontrolki Windows Forms do dokumentów i arkuszy w czasie projektowania, przeciągając kontrolki z **przybornika**lub w czasie wykonywania przy użyciu metod pomocnika. Jednak te narzędzia nie są dostępne dla formantów WPF.

Formanty WPF używają klasy <xref:System.Windows.Forms.Integration.ElementHost> jako warstwy integracji między formantem Windows Forms lub formularzem a kontrolkami WPF. Po dodaniu formantów WPF do rozwiązania w czasie projektowania program Visual Studio automatycznie generuje obiekt <xref:System.Windows.Forms.Integration.ElementHost>.

## <a name="wpf-resources"></a>Zasoby WPF

Aby uzyskać więcej informacji na temat problemów z architekturą i projektem na potrzeby hostowania formantów WPF na Windows Forms kontrolkach i formularzach, zobacz następujące tematy:

- [Architektura danych wejściowych współdziałania z Windows Forms i WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

- [Mapowanie właściwości Windows Forms i WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

- [WPF i Windows Forms międzyoperacyjności](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

- [Kontrolki Windows Forms i równoważne formanty WPF](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

Aby uzyskać więcej informacji na temat dodawania formantów WPF do Windows Forms formantów i formularzy w programie Visual Studio w czasie projektowania, zobacz następujące tematy:

- [Przewodnik: Tworzenie nowej zawartości WPF na Windows Forms w czasie projektowania](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

- [Przewodnik: rozmieszczanie zawartości WPF na Windows Forms w czasie projektowania](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

- [Przewodnik: zawartość w stylu WPF](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Kontrolki Windows Forms w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Przegląd okienka Akcje](../vsto/actions-pane-overview.md)
- [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Instrukcje: Dodawanie okienka akcji do dokumentów programu Word lub skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Instrukcje: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
