---
title: Powiązywanie kontrolek WPF z danymi (część 1) | Microsoft Docs
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
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 25b144409ae58f006602706a5b5cb498c0535ea2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540169"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Wiązanie kontrolek WPF z danymi w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz wyświetlić dane dla użytkowników aplikacji przez powiązanie danych z [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] kontrolkami. Aby utworzyć te kontrolki powiązane z danymi, możesz przeciągnąć elementy z okna **źródła danych** na [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . W tym temacie opisano niektóre typowe zadania, narzędzia i klasy, których można użyć do tworzenia aplikacji powiązanych z danymi [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] .

 Aby uzyskać ogólne informacje na temat sposobu tworzenia formantów powiązanych z danymi w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , zobacz [Powiązywanie formantów z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Aby uzyskać więcej informacji na temat [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] powiązania danych, zobacz temat [powiązanie danych — omówienie](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Zadania związane z wiązaniem formantów WPF z danymi
 Poniższa tabela zawiera listę zadań, które można wykonać, przeciągając elementy z okna **źródła danych** do [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] .

|Zadanie|Więcej informacji|
|----------|----------------------|
|Utwórz nowe formanty związane z danymi.<br /><br /> Powiąż istniejące formant z danymi.|[Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [POWIĄZYWANIE kontrolek WPF z zestawem danych](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Utwórz formant, które wyświetlają pokrewne dane w relacji nadrzędny podrzędny: kiedy użytkownik wybierze nadrzędny rekord danych w jednym formancie, inny formant wyświetli powiązane dane podrzędne dla wybranego rekordu.|[Wyświetlanie powiązanych danych w aplikacjach WPF](../data-tools/display-related-data-in-wpf-applications.md)|
|Utwórz *tabelę odnośników* , która wyświetla informacje z jednej tabeli na podstawie wartości pola klucza obcego w innej tabeli.|[Tworzenie tabel wyszukiwania w aplikacjach WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Powiąż formant z obrazem w bazie danych.|[Powiązywanie kontrolek z obrazami z bazy danych](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Prawidłowe elementy docelowe upuszczania
 Możesz przeciągnąć elementy w oknie **źródła danych** tylko do prawidłowych elementów docelowych upuszczania w [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] . Istnieją dwa główne rodzaje z prawidłowych miejsc upuszczania: kontenery i formanty. Kontener jest element interfejsu użytkownika, który zwykle zawiera formanty. Na przykład siatka jest kontenerem i podobnie okno.

## <a name="generated-xaml-and-code"></a>Wygenerowana XAML i kod
 Po przeciągnięciu elementu z okna **źródła danych** do [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] , program generuje, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] który definiuje nową kontrolkę powiązaną z danymi (lub wiąże istniejący formant ze źródłem danych). W przypadku niektórych źródeł danych program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje również kod w pliku związanym z kodem, który wypełnia źródło danych danymi.

 Poniższa tabela zawiera listę [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] kodów i [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generowanych dla każdego typu źródła danych w oknie **źródła danych** .

|Źródło danych|Generowanie pliku XAML, która wiąże formant ze źródłem danych|Generowanie kodu, który wypełnia źródło danych danymi|
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|
|Dataset|Tak|Tak|
|[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]|Tak|Tak|
|Usługa|Yes|Nie|
|Obiekt|Yes|Nie|

### <a name="datasets"></a>Zestawy danych
 Gdy przeciągniesz tabelę lub kolumnę z okna **źródła danych** do projektanta, generowane są [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] następujące elementy:

- Dodaje zestaw danych i nowy <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource>Jest obiektem, który może służyć do nawigowania i wyświetlania danych w zestawie danych.

- Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w projektancie, XAML powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, kod XAML utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant jest tworzony wewnątrz nowego <xref:System.Windows.Controls.Grid> .

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]wprowadza również następujące zmiany w pliku związanym z kodem:

- Tworzy <xref:System.Windows.FrameworkElement.Loaded> program obsługi zdarzeń dla [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)] elementu, który zawiera kontrolkę. Program obsługi zdarzeń wypełnia tabelę danymi, pobiera <xref:System.Windows.Data.CollectionViewSource> z zasobów kontenera, a następnie tworzy pierwszy element danych jako bieżący element. Jeśli <xref:System.Windows.FrameworkElement.Loaded> procedura obsługi zdarzeń już istnieje, program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dodaje ten kod do istniejącej procedury obsługi zdarzeń.

### <a name="entity-data-models"></a>Modele danych jednostek
 Podczas przeciągania jednostki lub właściwości jednostki z okna **źródła danych** do projektanta, program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] następujące elementy:

- Dodaje nowe <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource>Jest obiektem, który może służyć do nawigowania i wyświetlania danych w jednostce.

- Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w projektancie, obiekt [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, program [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant jest tworzony wewnątrz nowego <xref:System.Windows.Controls.Grid> .

  Visual Studio wprowadza następujące zmiany w pliku powiązanym z kodem:

- Dodaje nową metodę, która zwraca kwerendy dla elementu, który został przeciągnięty do projektanta (lub elementu zawierającego właściwość, która została przeciągnięta do projektanta). Nowa metoda ma nazwę get*EntityName*Query, gdzie *EntityName* jest nazwą obiektu.

- Tworzy <xref:System.Windows.FrameworkElement.Loaded> program obsługi zdarzeń dla [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)] elementu, który zawiera kontrolkę. Program obsługi zdarzeń wywołuje metodę get*EntityName*Query, aby wypełnić jednostkę danymi, pobiera <xref:System.Windows.Data.CollectionViewSource> z zasobów kontenera, a następnie tworzy pierwszy element danych jako bieżący element. Jeśli <xref:System.Windows.FrameworkElement.Loaded> procedura obsługi zdarzeń już istnieje, program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dodaje ten kod do istniejącej procedury obsługi zdarzeń.

### <a name="services"></a>Usługi
 Gdy przeciągasz obiekt usługi lub właściwość z okna **źródła danych** do projektanta, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] że tworzy formant powiązany z danymi (lub wiąże istniejący formant z obiektem lub właściwością). Jednak program nie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje kodu, który wypełnia obiekt usługi serwera proxy danymi. Musisz napisać ten kod samodzielnie. Aby zapoznać się z przykładem, który pokazuje, jak to zrobić, zobacz [Powiązywanie formantów WPF z usługą danych programu WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

 Visual Studio generuje plik XAML, który wykonuje następujące czynności:

- Dodaje nowe <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource>Jest obiektem, który może służyć do nawigowania i wyświetlania danych w obiekcie, który jest zwracany przez usługę.

- Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w projektancie, obiekt [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, program [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant jest tworzony wewnątrz nowego <xref:System.Windows.Controls.Grid> .

### <a name="objects"></a>Obiekty
 Gdy przeciągasz obiekt lub właściwość z okna **źródła danych** do projektanta, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] że tworzy formant powiązany z danymi (lub wiąże istniejący formant z obiektem lub właściwością). Jednak program nie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje kodu, który wypełnia obiekt danymi. Musisz napisać ten kod samodzielnie.

> [!NOTE]
> Klasy niestandardowe muszą być publiczne i domyślnie mają konstruktora bez parametrów. Nie mogą być klasami zagnieżdżonymi mającymi "kropkę" w ich składni. Aby uzyskać więcej informacji, zobacz [XAML i klasy niestandardowe dla WPF](https://msdn.microsoft.com/library/e7313137-581e-4a64-8453-d44e15a6164a).

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] , że program wykonuje następujące czynności:

- Dodaje nowe <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource>Jest obiektem, który może służyć do nawigowania i wyświetlania danych w obiekcie.

- Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w projektancie, XAML powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, kod XAML utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant jest tworzony wewnątrz nowego <xref:System.Windows.Controls.Grid> .

## <a name="see-also"></a>Zobacz też
 [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
