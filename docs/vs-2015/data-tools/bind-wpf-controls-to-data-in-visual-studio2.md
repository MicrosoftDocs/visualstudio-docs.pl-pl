---
title: Powiązywanie kontrolek WPF z danymi | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5c1733d6d4e60aad10896dbd2fcad16406830b83
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437038"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Powiązywanie kontrolek WPF z danymi w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można tworzyć powiązane z danymi [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] kontrolek przy użyciu **źródeł danych** okna. Najpierw Dodaj źródło danych w celu **źródeł danych** okna. Następnie przeciągnij elementy z **źródeł danych** okna**WPF Designer**.

## <a name="adding"></a> Dodawanie źródła danych do okna źródeł danych
 Zanim będzie można utworzyć formanty powiązane z danymi, należy najpierw dodać źródło danych w celu **źródeł danych** okna.

#### <a name="to-add-a-data-source-to-the-data-sources-window"></a>Aby dodać źródło danych do okna źródeł danych

1. Na **widoku** menu wskaż **Windows inne**, a następnie kliknij przycisk **źródeł danych**.

2. Kliknij przycisk **Dodaj nowe źródło danych**i wykonaj **konfiguracji źródła danych** kreatora.

3. Wykonaj jedną z następujących zadań w celu tworzenia formantów powiązanych z danymi:

    - [Tworzenie formantu, który jest powiązany z jednego pola danych](#simple).

    - [Tworzenie formantu, który jest powiązany z wielu pól danych](#complex).

    - [Tworzenie zestawu formantów, które są powiązane z wielu pól danych](#details).

    - [Powiązywanie danych z istniejących formantów w Projektancie](#existing).

## <a name="simple"></a> Utwórz formant, który jest powiązany z jednego pola danych
 Po dodaniu źródła danych do **źródeł danych** okna, można utworzyć nowego formantu powiązanych z danymi, który wyświetla jedno pole danych, takich jak <xref:System.Windows.Controls.ComboBox> lub <xref:System.Windows.Controls.TextBox>.

#### <a name="to-create-a-control-that-is-bound-to-a-single-field-of-data"></a>Aby utworzyć formant, który jest powiązany z jednego pola danych

1. W **źródeł danych** okna, rozwiń węzeł elementu, który reprezentuje tabeli lub obiektu. Znajdź element podrzędny, który reprezentuje kolumny lub właściwości, które chcesz powiązać z. Na przykład wizualny, zobacz [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Opcjonalnie wybierz formant Aby utworzyć. Każdy element na **źródeł danych** okno ma domyślny formant, który jest tworzony podczas przeciągania elementu do projektanta. Domyślny formant jest zależny od odpowiedniego typu danych elementu.

     Wybierz inny formant, kliknij strzałkę listy rozwijanej obok elementu i wybierz kontrolkę. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

3. Przeciągnij element do prawidłowego kontenera w projektancie. Aby uzyskać więcej informacji na temat kontenerów prawidłowy zobacz [WPF powiązać kontrolki z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tworzy nowy formant powiązany z danymi i odpowiednio zatytułowanym <xref:System.Windows.Controls.Label> w kontenerze. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje również [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] i kod, aby powiązać kontrolki z danymi. Aby uzyskać więcej informacji, zobacz [WPF powiązać kontrolki z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="complex"></a> Utwórz formant, który jest powiązany z wielu pól danych
 Po dodaniu źródła danych do **źródeł danych** okna, można utworzyć nowego formantu powiązanych z danymi, który zawiera wiele pól tych danych, takich jak <xref:System.Windows.Controls.DataGrid> lub <xref:System.Windows.Controls.ListView>.

#### <a name="to-create-a-control-that-is-bound-to-multiple-fields-of-data"></a>Aby utworzyć formant, który jest powiązany z wielu pól danych

1. W **źródeł danych** okna, wybierz element, który reprezentuje tabeli lub obiektu. Na przykład wizualny, zobacz [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Opcjonalnie wybierz formant Aby utworzyć. Domyślnie każdy element **źródeł danych** okna, który reprezentuje dane tabeli lub obiektu jest ustawiona na tworzenie <xref:System.Windows.Controls.DataGrid> (Jeśli projekt jest przeznaczony dla .NET Framework 4) lub <xref:System.Windows.Controls.ListView> (w przypadku wcześniejszych wersji programu .NET Framework).

     Aby wybrać inną kontrolkę, kliknij strzałkę listy rozwijanej obok elementu, a następnie wybierz kontrolkę. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    > [!NOTE]
    > Jeśli nie chcesz wyświetlać określonej kolumny lub właściwości, rozwiń element, aby wyświetlić jego elementy podrzędne. Kliknij strzałkę listy rozwijanej obok kolumny lub właściwości, które chcesz wyświetlić, a następnie kliknij przycisk **Brak**.

3. Przeciągnij element do prawidłowego kontenera w projektancie, takich jak <xref:System.Windows.Controls.Grid>. Aby uzyskać więcej informacji na temat kontenerów prawidłowy zobacz [WPF powiązać kontrolki z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tworzy nowy formant powiązany z danymi w kontenerze. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje również [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] i kod, aby powiązać kontrolki z danymi. Aby uzyskać więcej informacji, zobacz [WPF powiązać kontrolki z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="details"></a> Tworzenie zestawu formantów, które są powiązane z wielu pól danych
 Po dodaniu źródła danych do **źródeł danych** okna, można powiązać danych tabeli lub obiektu zbiór kontrolek. Innej kontrolki jest tworzona dla każdej kolumny lub właściwości w tabeli lub obiektu.

#### <a name="to-create-a-set-of-controls-that-are-bound-to-multiple-fields-of-data"></a>Aby utworzyć zestaw elementów sterujących, które są powiązane z wielu pól danych

1. W **źródeł danych** okna, wybierz element, który reprezentuje tabeli lub obiektu. Na przykład wizualny, zobacz [okna źródeł danych](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).

2. Kliknij strzałkę listy rozwijanej obok elementu i wybierz pozycję **szczegóły**.

    > [!NOTE]
    > Jeśli nie chcesz wyświetlać określonej kolumny lub właściwości, rozwiń element, aby wyświetlić jego elementy podrzędne. Kliknij strzałkę listy rozwijanej obok kolumny lub właściwości, które chcesz wyświetlić, a następnie kliknij przycisk **Brak**.

3. Przeciągnij element do prawidłowego kontenera w projektancie, takich jak <xref:System.Windows.Controls.Grid>. Aby uzyskać więcej informacji na temat kontenerów prawidłowy zobacz [WPF powiązać kontrolki z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tworzy nowe formanty powiązane z danymi w kontenerze. Każda kontrolka jest powiązana z innej kolumny lub właściwości, a każdy formant jest powiązany, odpowiednio zatytułowanym <xref:System.Windows.Controls.Label> kontroli. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje również [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] i kod, aby powiązać formanty z danymi. Aby uzyskać więcej informacji, zobacz [WPF powiązać kontrolki z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="existing"></a> Binddata istniejących formantów w Projektancie
 Po dodaniu źródła danych do **źródeł danych** okna, można dodać powiązania do istniejącego formantu w Projektancie danych.

#### <a name="to-bind-data-to-an-existing-control-in-the-designer"></a>Aby powiązać dane do istniejącego formantu w Projektancie

1. W **źródeł danych** okna, użyj jednej z następujących procedur:

    - Aby dodać powiązanie danych do istniejącego formantu, który wyświetla wiele pól tych danych, takich jak <xref:System.Windows.Controls.DataGrid> lub <xref:System.Windows.Controls.ListView>, zaznacz element, który odpowiada tabeli lub obiektu, że chcesz powiązać kontrolkę.

    - Aby dodać powiązanie danych do istniejącego formantu, który wyświetla jedno pole danych, takich jak <xref:System.Windows.Controls.ComboBox> lub <xref:System.Windows.Controls.TextBox>, rozwiń element który reprezentuje tabeli lub obiektu, który zawiera dane, a następnie wybierz element, który reprezentuje dane, które mają być Powiąż formant.

2. Przeciągnij zaznaczony element z **źródeł danych** okna do istniejącego formantu w projektancie. Kontrolka musi być prawidłową miejsca docelowego. Aby uzyskać więcej informacji, zobacz [WPF powiązać kontrolki z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] i kod, aby powiązać kontrolki z danymi. Aby uzyskać więcej informacji, zobacz [WPF powiązać kontrolki z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

    > [!NOTE]
    > Jeśli formant jest już powiązany z danymi, powiązanie danych kontrolki jest resetowany do elementu, który został ostatnio zostało przeciągnięte na formant.

## <a name="see-also"></a>Zobacz też
 [Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [Tworzenie tabel wyszukiwania w aplikacjach WPF](../data-tools/create-lookup-tables-in-wpf-applications.md) [wyświetlanie powiązanych danych w aplikacjach WPF](../data-tools/display-related-data-in-wpf-applications.md) [do zestawu danychformantypowiązaniaWPF](../data-tools/bind-wpf-controls-to-a-dataset.md) [WPF powiązać formanty do usługi danych WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) [instruktażu: Wyświetlanie powiązanych danych w aplikacji WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
