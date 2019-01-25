---
title: Użyj kontrolek WPF w rozwiązaniach pakietu Office
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
ms.openlocfilehash: 70c77e3b093947703680ab7253fdee0a6c3d60cd
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869765"
---
# <a name="use-wpf-controls-in-office-solutions"></a>Użyj kontrolek WPF w rozwiązaniach pakietu Office

Mimo że rozwiązań utworzonych przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio są przeznaczone do pracować bezpośrednio za pomocą kontrolek formularzy Windows Forms, umożliwia także kontrolek WPF w rozwiązaniach. Windows Presentation Foundation (WPF) stanowi alternatywę do formularzy Windows Forms, dotyczące projektowania interfejsów użytkownika. WPF używa języku znaczników o nazwie Extensible Application Markup Language (XAML), aby zapewnić nowych technik do włączania interfejsu użytkownika, multimedia i dokumenty. Aby uzyskać więcej informacji, zobacz [WPF — Przegląd](../designers/introduction-to-wpf.md).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

Dowolnego elementu interfejsu użytkownika, który może obsługiwać formantów formularzy Windows w rozwiązaniach pakietu Office może również obsługiwać kontrolek WPF. W tym następujące elementy:

-   Dokumenty i arkusze w dostosowaniach na poziomie dokumentu.

-   Okienka akcji w dostosowaniach na poziomie dokumentu.

-   Niestandardowe okienka zadań w dodatkach VSTO.

-   Regionów formularzy w dodatków narzędzi VSTO dla programu Outlook.

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>Dodawanie formantów WPF do projektów pakietu Office w czasie projektowania

Nie można dodać kontrolki WPF bezpośrednio do elementów interfejsu użytkownika w rozwiązaniach pakietu Office. Zamiast tego dodać **kontrolki użytkownika (WPF)** elementu do projektu i używać go jako powierzchni projektowej kontrolek WPF. Następnie należy dodać formanty użytkownika WPF z elementem interfejsu użytkownika w projekcie.

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Aby dodać formanty WPF do okienka akcji, region formularza lub niestandardowego okienka zadań

1.  Otwórz projekt, do której chcesz dodać niestandardowego okienka zadań, okienka akcji lub regionu formularza.

2.  Dodaj **kontrolki użytkownika (WPF)** elementu do projektu.

3.  Z **przybornika**, dodawanie formantów WPF do powierzchni projektowej kontrolki użytkownika WPF.

     Domyślnie, gdy projektant kontrolki użytkownika WPF jest otwarty **przybornika** zawiera tylko formanty WPF.

4.  Skompiluj projekt.

5.  Dodaj okienko akcji, region formularza lub niestandardowego okienka zadań do projektu:

    -   Dla regionów formularza należy dodać **Region formularza programu Outlook** do projektu. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

    -   Okienka akcji można dodać **kontrolki okienka akcji** lub **kontrolki użytkownika** do projektu. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie okienek akcji do dokumentów programu Word i skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md) i [jak: Dodawanie okienek akcji do dokumentów programu Word i skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

    -   Niestandardowe okienka zadań, można dodać **kontrolki użytkownika** do projektu. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

6.  Z *ProjectName* **kontrolek użytkownika WPF** karcie **przybornika**, przeciągnij formanty użytkownika WPF designer okienko akcji, region formularza lub niestandardowego okienka zadań.

     Program Visual Studio automatycznie tworzy <xref:System.Windows.Forms.Integration.ElementHost> obiektu, który obsługuje formanty użytkownika WPF w elemencie interfejsu użytkownika.

7.  Skompiluj ponownie projekt.

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Aby dodać formanty WPF do dokumentu lub arkusza w projekcie na poziomie dokumentu

1.  Otwórz projekt poziomie dokumentu dla programu Word lub Excel.

2.  Dodaj **kontrolki użytkownika (WPF)** elementu do projektu.

3.  Z **przybornika**, dodawanie formantów WPF do powierzchni projektowej kontrolki użytkownika WPF.

4.  Skompiluj projekt.

5.  Dodaj **kontrolki użytkownika** elementu (oznacza to, że formant użytkownika interfejsu Windows Forms) do projektu.

6.  Otwórz projektanta dla kontrolki użytkownika Windows Forms.

7.  Z *ProjectName* **kontrolek użytkownika WPF** karcie **przybornika**, przeciągnij formanty użytkownika WPF do projektanta.

     Program Visual Studio automatycznie tworzy <xref:System.Windows.Forms.Integration.ElementHost> obiektu, który obsługuje formanty użytkownika WPF w kontrolce użytkownika Windows Forms.

8.  Napisz kod, który programowo dodaje kontrolki użytkownika Windows Forms do dokumentów lub skoroszycie. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).

    > [!NOTE]
    > Nie można przeciągnąć kontrolki użytkownika Windows Forms do dokumentu lub arkusza w projektancie.

9. Skompiluj ponownie projekt.

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>Host formantów WPF za pomocą klasy ElementHost

Visual Studio zawiera funkcje, które ułatwiają użyć kontrolek formularzy Windows Forms w rozwiązaniach pakietu Office, ale nie zapewnia podobne funkcje dla kontrolek WPF. Na przykład, możesz dodać kontrolek formularzy Windows Forms do dokumentów i arkuszy w czasie projektowania poprzez przeciąganie kontrolek z **przybornika**, lub w czasie wykonywania za pomocą metody pomocnika. Jednak te narzędzia nie są dostępne w przypadku kontrolek WPF.

WPF steruje użyciem <xref:System.Windows.Forms.Integration.ElementHost> klasy jako warstwa integracji między formantu Windows Forms lub formularzy i kontrolek WPF. Po dodaniu kontrolki WPF do rozwiązania w czasie projektowania program Visual Studio automatycznie generuje <xref:System.Windows.Forms.Integration.ElementHost> obiekt dla Ciebie.

## <a name="wpf-resources"></a>Zasoby programu WPF

Aby uzyskać więcej informacji na temat architektury i zagadnienia dotyczące projektowania dla hostingu kontrolek WPF w formularzach i kontrolek formularzy Windows Forms zobacz następujące tematy:

-   [Windows Forms i WPF wejścia ze zdolnością](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

-   [Mapowanie właściwości Windows Forms i WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

-   [Współdziałanie WPF i Windows Forms](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

-   [Kontroluje kontrolek formularzy Windows Forms i równoważne WPF](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

Aby uzyskać więcej informacji na temat dodawania formantów WPF do kontrolek formularzy Windows Forms i formularzy w programie Visual Studio w czasie projektowania zobacz następujące tematy:

-   [Przewodnik: Tworzenie nowej zawartości WPF na formularzach Windows Forms w czasie projektowania](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

-   [Przewodnik: Rozmieszczanie zawartości WPF na formularzach Windows Forms w czasie projektowania](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

-   [Przewodnik: Stylu zawartości WPF](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Formanty Windows Forms na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)
- [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Instrukcje: Dodawanie okienek akcji do dokumentów programu Word lub arkuszy programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Instrukcje: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
