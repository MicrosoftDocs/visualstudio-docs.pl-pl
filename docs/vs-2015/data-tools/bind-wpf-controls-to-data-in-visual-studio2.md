---
title: Powiązywanie kontrolek WPF z danymi (część 2) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06428a633aec41489a8a77655d6ea9442ffffaa0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540091"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Wiązanie kontrolek WPF z danymi w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Formanty powiązane z danymi można tworzyć przy [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] użyciu okna **źródła danych** . Najpierw Dodaj źródło danych do okna **źródła danych** . Następnie przeciągnij elementy z okna **źródła danych** do**projektanta WPF**.

## <a name="add-a-data-source-to-the-data-sources-window"></a><a name="adding"></a> Dodawanie źródła danych do okna źródła danych
 Aby można było tworzyć kontrolki powiązane z danymi, należy najpierw dodać źródło danych do okna **źródła danych** .

#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>Aby dodać źródło danych do okna źródła danych

1. W menu **Widok** wskaż polecenie **inne okna**, a następnie kliknij pozycję **źródła danych**.

2. Kliknij przycisk **Dodaj nowe źródło danych**i Ukończ pracę kreatora **konfiguracji źródła danych** .

3. Wykonaj jedno z następujących zadań, aby utworzyć formanty powiązane z danymi:

    - [Tworzenie kontrolki, która jest powiązana z pojedynczym polem danych](#simple).

    - [Tworzenie kontrolki, która jest powiązana z wieloma polami danych](#complex).

    - [Tworzenie zestawu formantów, które są powiązane z wieloma polami danych](#details).

    - [Powiązanie danych z istniejącymi kontrolkami w projektancie](#existing).

## <a name="create-a-control-that-is-bound-to-a-single-field-of-data"></a><a name="simple"></a> Utwórz formant, który jest powiązany z pojedynczym polem danych
 Po dodaniu źródła danych do okna **źródła danych** można utworzyć nową kontrolkę powiązaną z danymi, która wyświetla pojedyncze pole danych, takie jak <xref:System.Windows.Controls.ComboBox> lub <xref:System.Windows.Controls.TextBox> .

#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>Aby utworzyć formant, który jest powiązany z pojedynczym polem danych

1. W oknie **źródła danych** rozwiń element, który reprezentuje tabelę lub obiekt. Znajdź element podrzędny reprezentujący kolumnę lub właściwość, do której chcesz utworzyć powiązanie. Aby zapoznać się z przykładem wizualizacji, zobacz [okno źródła danych](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Opcjonalnie wybierz kontrolkę, którą chcesz utworzyć. Każdy element w oknie **źródła danych** ma formant domyślny, który jest tworzony podczas przeciągania elementu do projektanta. Domyślny formant zależy od bazowego typu danych elementu.

     Aby wybrać inny formant, kliknij strzałkę listy rozwijanej obok elementu i wybierz kontrolkę. Aby uzyskać więcej informacji, zobacz [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródła danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

3. Przeciągnij element do prawidłowego kontenera w projektancie. Aby uzyskać więcej informacji na temat prawidłowych kontenerów, zobacz [Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tworzy nową kontrolkę powiązaną z danymi i odpowiednio zatytułowaną <xref:System.Windows.Controls.Label> w kontenerze. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje również [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] kod, aby powiązać formant z danymi. Aby uzyskać więcej informacji, zobacz [Powiązywanie formantów WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="create-a-control-that-is-bound-to-multiple-fields-of-data"></a><a name="complex"></a> Tworzenie kontrolki, która jest powiązana z wieloma polami danych
 Po dodaniu źródła danych do okna **źródła danych** można utworzyć nową kontrolkę powiązaną z danymi, która wyświetla wiele pól danych, takich jak <xref:System.Windows.Controls.DataGrid> lub <xref:System.Windows.Controls.ListView> .

#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>Aby utworzyć formant, który jest powiązany z wieloma polami danych

1. W oknie **źródła danych** wybierz element, który reprezentuje tabelę lub obiekt. Aby zapoznać się z przykładem wizualizacji, zobacz [okno źródła danych](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Opcjonalnie wybierz kontrolkę, którą chcesz utworzyć. Domyślnie każdy element w oknie **źródła danych** , który reprezentuje tabelę lub obiekt danych, jest ustawiony do tworzenia <xref:System.Windows.Controls.DataGrid> (Jeśli projekt jest przeznaczony .NET Framework 4) lub <xref:System.Windows.Controls.ListView> (dla wcześniejszych wersji .NET Framework).

     Aby wybrać inny formant, kliknij strzałkę listy rozwijanej obok elementu i wybierz kontrolkę. Aby uzyskać więcej informacji, zobacz [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródła danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    > [!NOTE]
    > Jeśli nie chcesz wyświetlać określonej kolumny lub właściwości, rozwiń element, aby wyświetlić jego elementy podrzędne. Kliknij strzałkę listy rozwijanej obok kolumny lub właściwości, których nie chcesz wyświetlać, a następnie kliknij pozycję **Brak**.

3. Przeciągnij element do prawidłowego kontenera w projektancie, na przykład <xref:System.Windows.Controls.Grid> . Aby uzyskać więcej informacji na temat prawidłowych kontenerów, zobacz [Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tworzy nową kontrolkę powiązaną z danymi w kontenerze. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje również [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] kod, aby powiązać formant z danymi. Aby uzyskać więcej informacji, zobacz [Powiązywanie formantów WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a><a name="details"></a> Tworzenie zestawu formantów, które są powiązane z wieloma polami danych
 Po dodaniu źródła danych do okna **źródła danych** można powiązać tabelę danych lub obiekt z zestawem kontrolek. Dla każdej kolumny lub właściwości w tabeli lub obiekcie tworzony jest inny formant.

#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>Aby utworzyć zestaw formantów, które są powiązane z wieloma polami danych

1. W oknie **źródła danych** wybierz element, który reprezentuje tabelę lub obiekt. Aby zapoznać się z przykładem wizualizacji, zobacz [okno źródła danych](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Kliknij strzałkę listy rozwijanej obok elementu i wybierz pozycję **szczegóły**.

    > [!NOTE]
    > Jeśli nie chcesz wyświetlać określonej kolumny lub właściwości, rozwiń element, aby wyświetlić jego elementy podrzędne. Kliknij strzałkę listy rozwijanej obok kolumny lub właściwości, których nie chcesz wyświetlać, a następnie kliknij pozycję **Brak**.

3. Przeciągnij element do prawidłowego kontenera w projektancie, na przykład <xref:System.Windows.Controls.Grid> . Aby uzyskać więcej informacji na temat prawidłowych kontenerów, zobacz [Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tworzy nowe kontrolki powiązane z danymi w kontenerze. Każda kontrolka jest powiązana z inną kolumną lub właściwością, a każda z nich towarzyszy odpowiednio zatytułowanej <xref:System.Windows.Controls.Label> kontrolki. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje również [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] kod, aby powiązać kontrolki z danymi. Aby uzyskać więcej informacji, zobacz [Powiązywanie formantów WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="binddata-to-existing-controls-in-the-designer"></a><a name="existing"></a> Binddata do istniejących kontrolek w projektancie
 Po dodaniu źródła danych do okna **źródła danych** można dodać powiązanie danych do istniejącej kontrolki w projektancie.

#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>Aby powiązać dane z istniejącą kontrolką w projektancie

1. W oknie **źródła danych** Użyj jednej z następujących procedur:

    - Aby dodać powiązanie danych do istniejącej kontrolki, która wyświetla wiele pól danych, takich jak <xref:System.Windows.Controls.DataGrid> lub <xref:System.Windows.Controls.ListView> , zaznacz element reprezentujący tabelę lub obiekt, który chcesz powiązać z kontrolką.

    - Aby dodać powiązanie danych do istniejącej kontrolki, która wyświetla pojedyncze pole danych, takie jak <xref:System.Windows.Controls.ComboBox> lub <xref:System.Windows.Controls.TextBox> , rozwiń element reprezentujący tabelę lub obiekt, który zawiera dane, a następnie wybierz element reprezentujący dane, które chcesz powiązać z kontrolką.

2. Przeciągnij wybrany element z okna **źródła danych** na istniejący formant w projektancie. Formant musi być prawidłowym miejscem docelowym upuszczania. Aby uzyskać więcej informacji, zobacz [Powiązywanie formantów WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] i kodu, aby powiązać formant z danymi. Aby uzyskać więcej informacji, zobacz [Powiązywanie formantów WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

    > [!NOTE]
    > Jeśli kontrolka jest już powiązana z danymi, powiązanie danych dla kontrolki jest resetowane do elementu, który został przeciągnięty do formantu ostatnio.

## <a name="see-also"></a>Zobacz też
 [Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [Tworzenie tabel wyszukiwania w aplikacjach WPF](../data-tools/create-lookup-tables-in-wpf-applications.md) [Wyświetlanie powiązanych danych w aplikacjach WPF](../data-tools/display-related-data-in-wpf-applications.md) [Powiązywanie formantów WPF z zestawem](../data-tools/bind-wpf-controls-to-a-dataset.md) danych [POWIĄZYWANIE formantów WPF z przewodnikiem usługi danych programu WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [: wyświetlanie powiązanych danych w aplikacji WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
