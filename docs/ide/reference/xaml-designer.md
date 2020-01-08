---
title: Strona opcji projektant XAML
ms.date: 03/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.XAMLDesigner
- VS.ToolsOptionsPages.XAML_Designer.General
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 9a925e7f3c31b8347148c15b050692fcee26fcb1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585616"
---
# <a name="xaml-designer-options-page"></a>Strona opcji projektant XAML

Na stronie opcje **Projektant XAML** można określić sposób formatowania elementów i atrybutów w dokumentach XAML. Aby otworzyć tę stronę, wybierz menu **Narzędzia** , a następnie wybierz polecenie **Opcje**. Aby uzyskać dostęp do strony właściwości **Projektant XAML** , wybierz węzeł **Projektant XAML** . Ustawienia dla projektant XAML są stosowane po otwarciu dokumentu. Dlatego jeśli wprowadzisz zmiany w ustawieniach, musisz zamknąć i ponownie otworzyć program Visual Studio, aby zobaczyć zmiany.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../environment-settings.md#reset-settings).

## <a name="enable-xaml-designer"></a>Włącz projektant XAML

Po wybraniu tego ustawienia włącza projektant XAML. Projektant XAML udostępnia obszar roboczy wizualizacji, w którym można edytować dokumenty XAML. Niektóre funkcje w programie Visual Studio, takie jak IntelliSense dla zasobów i danych DataBinding, wymagają włączenia projektant XAML.

Poniższe ustawienia są stosowane tylko wtedy, gdy projektant XAML jest włączona. Jeśli zmienisz tę opcję, konieczne będzie ponowne uruchomienie programu Visual Studio, aby ustawienie zaczęło obowiązywać.

## <a name="default-document-view"></a>Widok dokumentu domyślnego

Użyj tego ustawienia, aby określić, czy widok Projekt pojawia się po załadowaniu dokumentów XAML.

|||
|-|-|
|**Widok źródła**|Określa, czy tylko źródło XAML jest wyświetlane w widoku XAML. Jest to przydatne podczas ładowania dużych dokumentów.|
|**Widok projektu**|Określa, czy tylko projektant XAML wizualizacji ma być wyświetlana w widoku XAML.|
|**Widok podzielony**|Określa, czy element wizualny projektant XAML i źródło XAML będą widoczne obok siebie w widoku XAML (lokalizacja na podstawie ustawienia **orientacji podziału** ).|

## <a name="split-orientation"></a>Podziel orientację

Użyj tego ustawienia, aby określić, kiedy i jak projektant XAML pojawia się podczas edytowania dokumentu XAML. Te ustawienia są stosowane tylko wtedy, gdy **widok dokumentu domyślnego** jest ustawiony na **Widok podzielony**.

|||
|-|-|
|**Pionow**|Źródło XAML pojawia się po lewej stronie widoku XAML, a projektant XAML pojawia się po drugiej stronie.|
|**Układ**|Projektant XAML pojawia się w górnej części widoku XAML, a źródło XAML pojawia się poniżej.|
|**Default**|Dokument XAML stosuje orientację podziału zalecaną dla platformy wskazywanej przez projekt dokumentu. W przypadku większości platform jest to odpowiednik w **poziomie**.|

## <a name="zoom-by-using"></a>Powiększ przy użyciu

Użyj tego ustawienia, aby określić, jak powiększenie ma być stosowane podczas edytowania dokumentu XAML.

|||
|-|-|
|**Kółko myszy**|Powiększ projektant XAML, przewijając kółko myszy.|
|**CTRL + kółko myszy**|Powiększ projektant XAML, naciskając klawisz **Ctrl** podczas przewijania kółka myszy.|
|**Alt + kółko myszy**|Powiększ projektant XAML, naciskając klawisz **Alt** podczas przewijania kółka myszy.|

Te ustawienia określają zachowanie projektanta podczas edytowania dokumentu XAML.

|||
|-|-|
|**Automatycznie Nazwij elementy interaktywne podczas tworzenia**|Określa, czy nazwa domyślna jest pokazana dla nowego elementu interaktywnego po dodaniu go do projektanta.|
|**Automatycznie Wstaw właściwości układu podczas tworzenia elementu**|Określa, czy właściwości układu są udostępniane dla nowego elementu po dodaniu go do projektanta. Właściwości układu to te, które wpływają na układ kontrolki, na przykład Margin i VerticalAlignment. Poniższy kod XAML pokazuje, w jaki sposób przycisk jest tworzony z i bez wybrania tej opcji:<br />`<Button Content="Button" HorizontalAlignment="Left" Margin="245,56,0,0" Grid.Row="1" VerticalAlignment="Top" Width="75"/>`<br />`<Button Content="Button" Grid.Row="1"/>`|
|**Korzystanie z układu opartego na ćwiartki**|Określa, czy aktualnie wybrana kontrolka jest wyrównana do najbliższej krawędzi kontenera nadrzędnego. Jeśli to pole wyboru jest wyczyszczone, wyrównania formantów nie są zmieniane podczas operacji przenoszenia lub tworzenia.|
|**Automatycznie Wypełnij elementy przybornika**|Określa, czy kontrolki użytkownika i kontrolki niestandardowe w bieżącym rozwiązaniu są automatycznie wyświetlane w przyborniku.|

## <a name="settings-blend-only"></a>Ustawienia (tylko Blend)

Użyj tych opcji, aby określić ustawienia podczas edytowania plików XAML przy użyciu programu Blend.

|||
|-|-|
|**Powiększ przy użyciu**|Powiększ projektant XAML przez przewinięcie kółka myszy lub naciśnięcie klawisza **Ctrl** lub **Alt** podczas przewijania kółka myszy.|
|**Jednostki typu**|Określa, czy pomiary projektanta są oparte na punktach lub pikselach. Ponieważ aplikacje uniwersalne systemu Windows nie obsługują punktów, jednostki są automatycznie konwertowane na piksele w przypadku wybrania **punktów** .|

## <a name="artboard-blend-only"></a>Obszar kompozycji (tylko Blend)

Użyj tych ustawień, aby określić zachowanie projektant XAML podczas edytowania dokumentów XAML w programie Blend.

### <a name="snapping"></a>Przyciąganie

|||
|-|-|
|**Pokaż siatkę przyciągania**|Gdy ta opcja jest zaznaczona, linie siatki są wyświetlane w projektancie, aby ułatwić wyrównywanie kontrolek. Formanty dodane do przyciągania projektanta do tych linii siatki, gdy zaznaczona jest opcja **Przyciągaj do linii siatki** .|
|**Przyciągaj do linii siatki**|Gdy formanty są dodawane lub przenoszone wokół projektanta, są one przyciągane do linii siatki.|
|**Odstępy linii siatki**|Określa odstępy między liniami siatki w pikselach lub punktach (zgodnie z ustawieniem **jednostki typu** ).|
|**Przyciągaj do linii wyrównania**|Określa, czy formanty mają być przyciągane do linii wyrównania.|
|**Domyślny margines**|Po włączeniu **przyciągania do linii wyrównania** określa odstępy między kontrolką a linii wyrównania w pikselach lub punktach (zgodnie z ustawieniem **jednostki typu** ).|
|**Domyślne dopełnienie**|Po włączeniu **przyciągania do linii wyrównania** określa dodatkowe odstępy między kontrolką a linii wyrównania w pikselach lub punktach (zgodnie z ustawieniem **jednostki typu** ).|

### <a name="animation"></a>Animacja

Użyj tego ustawienia, aby określić, czy ostrzeżenie ma być wyświetlane, gdy w programie Blend są włączone animacje zależne (bez przyspieszania).

### <a name="effects"></a>Efekty

Użyj tych ustawień, aby określić, czy efekty są renderowane podczas edytowania plików XAML w projektant XAML przy użyciu programu Blend.

|||
|-|-|
|**Efekty renderowania**|Określa, czy efekty mają być renderowane podczas edytowania plików XAML w projektant XAML przy użyciu programu Blend.|
|**Próg powiększenia**|Określa wartość procentową powiększania efektów renderowania, gdy zaznaczone jest pole wyboru **efekty renderowania** . Jeśli powiększysz wartość tego ustawienia, efekty nie będą już renderowane w projektant XAML.|

## <a name="see-also"></a>Zobacz także

- [XAML w WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Przewodnik: moja pierwsza aplikacja klasyczna WPF](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)
