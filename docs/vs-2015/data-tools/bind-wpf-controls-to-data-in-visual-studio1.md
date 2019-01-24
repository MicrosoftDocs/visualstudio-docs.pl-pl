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
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: aeed612c94064eb9a364f9aa1d5fb6332bb0e77d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766894"
---
# <a name="bind-wpf-controls-to-data-in-visual-studio"></a>Powiązywanie kontrolek WPF z danymi w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Można wyświetlić dane użytkownikom aplikacji przez powiązanie danych z [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] kontrolki. Aby utworzyć te formanty powiązane z danymi, można przeciągnąć elementy z **źródeł danych** okna na [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)] w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. W tym temacie opisano niektóre z najbardziej typowych zadań, narzędzi i klas, które służą do tworzenia powiązanych z danymi [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] aplikacji.

 Aby uzyskać ogólne informacje o sposobie tworzenia formantów powiązanych z danymi w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], zobacz [powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Aby uzyskać więcej informacji na temat [!INCLUDE[TLA#tla_titlewinclient](../includes/tlasharptla-titlewinclient-md.md)] wiązania danych, zobacz [Data Binding Overview](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="tasks-involved-in-binding-wpf-controls-to-data"></a>Zadania związane z wiązaniem formantów WPF z danymi
 Poniższa tabela zawiera listę zadań, które można wykonać przez przeciąganie elementów z **źródeł danych** okna [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)].

|Zadanie|Więcej informacji|
|----------|----------------------|
|Utwórz nowe formanty związane z danymi.<br /><br /> Powiąż istniejące formant z danymi.|[Powiązywanie kontrolek WPF z danymi w programie Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [WPF powiązać formanty do zestawu danych](../data-tools/bind-wpf-controls-to-a-dataset.md)|
|Utwórz formant, które wyświetlają pokrewne dane w relacji nadrzędny podrzędny: kiedy użytkownik wybierze nadrzędny rekord danych w jednym formancie, inny formant wyświetli powiązane dane podrzędne dla wybranego rekordu.|[Wyświetlanie powiązanych danych w aplikacjach WPF](../data-tools/display-related-data-in-wpf-applications.md)|
|Tworzenie *tabeli odnośników* wyświetlającą informacje z jednej tabeli na podstawie wartości pola klucza obcego w innej tabeli.|[Tworzenie tabel wyszukiwania w aplikacjach WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|
|Powiąż formant z obrazem w bazie danych.|[Powiązywanie kontrolek z obrazami z bazy danych](../data-tools/bind-controls-to-pictures-from-a-database.md)|

## <a name="valid-drop-targets"></a>Prawidłowe miejsca upuszczania
 Można przeciągnąć elementy w **źródeł danych** okna tylko prawidłowe miejsca upuszczania w [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)]. Istnieją dwa główne rodzaje z prawidłowych miejsc upuszczania: kontenery i formanty. Kontener jest element interfejsu użytkownika, który zwykle zawiera formanty. Na przykład siatka jest kontenerem i podobnie okno.

## <a name="generated-xaml-and-code"></a>Wygenerowany XAML i kodu
 Podczas przeciągania elementu z **źródeł danych** okna [!INCLUDE[wpfdesigner_current_short](../includes/wpfdesigner-current-short-md.md)], [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] definiuje nowy formant powiązany z danymi (lub wiąże istniejący formant ze źródłem danych). Dla niektórych źródeł danych [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] również generuje kod w pliku związanym z kodem, który wypełnia źródło danych danymi.

 W poniższej tabeli wymieniono [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] i kod, który [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dla każdego typu źródła danych w **źródeł danych** okna.

|Źródło danych|Generowanie pliku XAML, która wiąże formant ze źródłem danych|Generowanie kodu, który wypełnia źródło danych danymi|
|-----------------|-----------------------------------------------------------|--------------------------------------------------------|
|Zestaw danych|Tak|Yes|
|[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]|Yes|Tak|
|Usługa|Tak|Nie|
|Obiekt|Tak|Nie|

### <a name="datasets"></a>Zestawy danych
 Podczas przeciągania tabeli lub kolumny z **źródeł danych** okna Projektanta [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] wykonujący następujące czynności:

- Dodaje zestaw danych i nową <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource> Jest obiektem, który może służyć do nawigowania i wyświetlania danych w zestawie danych.

- Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w projektancie, XAML powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, XAML utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant zostanie utworzony wewnątrz nowego <xref:System.Windows.Controls.Grid>.

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sprawia, że następujące zmiany w pliku związanym z kodem:

- Tworzy <xref:System.Windows.FrameworkElement.Loaded> program obsługi zdarzeń dla [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)] element, który zawiera formant. Program obsługi zdarzeń wypełnia tabelę z danymi, pobiera <xref:System.Windows.Data.CollectionViewSource> z kontenera zasobów, a następnie sprawia, że pierwszy element danych jako bieżący. Jeśli <xref:System.Windows.FrameworkElement.Loaded> istnieje już program obsługi zdarzeń, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dodaje ten kod do istniejącego programu obsługi zdarzeń.

### <a name="entity-data-models"></a>Jednostki danych modeli
 Podczas przeciągania jednostki lub właściwości jednostki z **źródeł danych** okna Projektanta [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] wykonujący następujące czynności:

- Dodaje nowy <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource> Jest obiektem, który może służyć do nawigowania i wyświetlić dane w jednostce.

- Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w Projektancie [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant zostanie utworzony wewnątrz nowego <xref:System.Windows.Controls.Grid>.

  Visual Studio wprowadza następujące zmiany w pliku powiązanym z kodem:

- Dodaje nową metodę, która zwraca kwerendy dla elementu, który został przeciągnięty do projektanta (lub elementu zawierającego właściwość, która została przeciągnięta do projektanta). Nowa metoda ma nazwę Get*EntityName*zapytania, gdzie *EntityName* jest nazwą obiektu.

- Tworzy <xref:System.Windows.FrameworkElement.Loaded> program obsługi zdarzeń dla [!INCLUDE[TLA2#tla_ui](../includes/tla2sharptla-ui-md.md)] element, który zawiera formant. Program obsługi zdarzeń wywołuje Get*EntityName*metody w celu wypełnienia elementu danymi, pobiera zapytania <xref:System.Windows.Data.CollectionViewSource> z kontenera zasobów, a następnie sprawia, że pierwszy element danych jako bieżący. Jeśli <xref:System.Windows.FrameworkElement.Loaded> istnieje już program obsługi zdarzeń, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dodaje ten kod do istniejącego programu obsługi zdarzeń.

### <a name="services"></a>Usługi
 Podczas przeciągania obiektu usługi lub właściwości z **źródeł danych** okna Projektanta [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] tworzący formant powiązany z danymi (lub wiąże istniejący formant z obiektem lub właściwością). Jednak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie generuje kodu, który wypełnia obiekt usługi serwera proxy danymi. Musisz napisać ten kod samodzielnie. Na przykład, który pokazuje, jak to zrobić, zobacz [WPF powiązać formanty do usługi danych WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

 Visual Studio generuje plik XAML, który wykonuje następujące czynności:

-   Dodaje nowy <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource> Jest obiektem, który może służyć do nawigowania i wyświetlania danych w obiekcie, który jest zwracany przez usługę.

-   Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w Projektancie [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant zostanie utworzony wewnątrz nowego <xref:System.Windows.Controls.Grid>.

### <a name="objects"></a>Obiekty
 Podczas przeciągania obiektu lub właściwości z **źródeł danych** okna Projektanta [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] tworzący formant powiązany z danymi (lub wiąże istniejący formant z obiektem lub właściwością). Jednak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje kodu, który wypełnia obiekt danych. Musisz napisać ten kod samodzielnie.

> [!NOTE]
>  Klasy niestandardowe muszą być publiczne i domyślnie ma konstruktora bez parametrów. Nie mogą one być klasami zagnieżdżonymi, które mają "dot" w ich składnię. Aby uzyskać więcej informacji, zobacz [XAML oraz klas niestandardowe dla WPF](http://msdn.microsoft.com/library/e7313137-581e-4a64-8453-d44e15a6164a).

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] wykonujący następujące czynności:

-   Dodaje nowy <xref:System.Windows.Data.CollectionViewSource> do zasobów kontenera, do którego został przeciągnięty element. <xref:System.Windows.Data.CollectionViewSource> Jest obiektem, który może służyć do nawigowania i wyświetlania danych w obiekcie.

-   Tworzy wiązania danych dla formantu. Jeśli przeciągniesz element do istniejącego formantu w projektancie, XAML powiąże formant z elementem. Jeśli przeciągniesz element do kontenera, XAML utworzy formant, który został wybrany dla przeciąganego elementu i powiąże formant z elementem. Formant zostanie utworzony wewnątrz nowego <xref:System.Windows.Controls.Grid>.

## <a name="see-also"></a>Zobacz też
 [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
