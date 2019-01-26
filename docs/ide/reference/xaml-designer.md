---
title: Strona Opcje projektanta XAML
ms.date: 03/02/2017
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.XAMLDesigner
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 907ead76b91048967c50c7e4c4460d8f68ac0c7b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938123"
---
# <a name="xaml-designer-options-page"></a>Strona Opcje projektanta XAML

Użyj **projektanta XAML** Strona opcji, aby określić, jak sformatowane elementów i atrybutów w dokumencie XAML. Aby otworzyć tę stronę, wybierz **narzędzia** menu, a następnie wybierz **opcje**. Aby uzyskać dostęp do **projektanta XAML** właściwości wybierz **projektanta XAML** węzła. Ustawienia projektanta XAML są stosowane po otwarciu dokumentu. Dlatego jeśli wprowadzisz zmiany w ustawieniach należy zamknąć i ponownie otworzyć programu Visual Studio, aby zobaczyć zmiany.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../environment-settings.md#reset-settings).

## <a name="enable-xaml-designer"></a>Włącz projektanta XAML

Po wybraniu tego ustawienia umożliwia projektanta XAML. Projektant XAML zawiera obszar roboczy visual do edycji dokumenty XAML. Niektóre funkcje w programie Visual Studio, takie jak IntelliSense zasobów lub powiązań danych, wymagają włączenia projektanta XAML.

Następujące ustawienia są stosowane tylko wtedy, gdy projektant XAML został włączony. Jeśli zmienisz tę opcję, konieczne będzie ponowne uruchomienie programu Visual Studio dla ustawienia zaczęły obowiązywać.

## <a name="default-document-view"></a>Domyślny widok dokumentu

Użyj to ustawienie, aby określić, czy widok projektu jest wyświetlany, gdy dokumenty XAML są ładowane.

|||
|-|-|
|**Widok źródła**|Określa, czy tylko źródła XAML jest wyświetlana w widoku XAML. Jest to przydatne w przypadku ładowania dużych dokumentów.|
|**Widok projektu**|Określa, czy tylko element wizualny Projektant XAML jest wyświetlana w widoku XAML.|
|**Widok podzielony**|Określa, czy zarówno wizualnego projektanta XAML i źródła XAML są wyświetlane obok siebie w widoku XAML (na podstawie lokalizacji **orientacji podziału** ustawienie).|

## <a name="split-orientation"></a>Rientacja podziału

To ustawienie służy do kontrolowania, kiedy i jak projektant XAML jest wyświetlana podczas edycji dokumentu XAML. Te ustawienia mają zastosowanie tylko wtedy, gdy **domyślny widok dokumentu** ustawiono **widoku złożonego**.

|||
|-|-|
|**W pionie**|Źródło XAML jest wyświetlana po lewej stronie w widoku XAML, a po drugiej stronie pojawi się okno projektanta XAML.|
|**Horizontal**|Projektant XAML jest wyświetlana u góry widoku XAML, a źródła XAML jest wyświetlana poniżej.|
|**Default**|Dokument XAML używa orientacji podziału zalecane dla platformy docelowej projektu dokumentu. Dla większości platform jest to równoważne **poziomy**.|

## <a name="zoom-by-using"></a>Powiększ za pomocą

Użyj tego ustawienia, aby określić, jak powiększenia działa podczas edycji dokumentu XAML.

|||
|-|-|
|**Obrót kółkiem myszy**|Powiększenie w Projektancie XAML przy użyciu kółka myszy.|
|**Ctrl + kółko myszy**|Powiększenie w Projektancie XAML, naciskając klawisz **Ctrl** klucza przy użyciu kółka myszy.|
|**ALT + myszy koło**|Powiększenie w Projektancie XAML, naciskając klawisz **Alt** klucza przy użyciu kółka myszy.|

Te ustawienia określają zachowanie projektanta podczas edycji dokumentu XAML.

|||
|-|-|
|**Automatycznie nadawać nazwy elementom interaktywnym podczas ich tworzenia**|Określa, czy nazwa domyślna jest dostarczany dla nowego elementu interaktywne po dodaniu do projektanta.|
|**Automatycznie Wstaw właściwości układu podczas tworzenia elementu**|Określa, czy właściwości układu są dostarczane dla nowego elementu, gdy możesz dodać do projektanta. Właściwości układu są te, które mają wpływ na układ formantu, na przykład, marża i VerticalAlignment. Następujące XAML pokazuje, jak przycisk jest tworzony i bez wybrania tej opcji:<br />`<Button Content="Button" HorizontalAlignment="Left" Margin="245,56,0,0" Grid.Row="1" VerticalAlignment="Top" Width="75"/>`<br />`<Button Content="Button" Grid.Row="1"/>`|
|**Użyj quadrant na podstawie układu**|Określa, czy aktualnie wybraną kontrolkę wyrównuje do najbliższej krawędzi kontenera nadrzędnego. Jeśli to pole wyboru jest wyczyszczone, wyrównanie kontrolki nie zmieniać podczas przenoszenia lub operacji tworzenia.|
|**Automatycznie wypełnij elementy przybornika**|Określa, czy kontrolki użytkownika i niestandardowe formanty w bieżącym rozwiązaniu są wyświetlane w przyborniku automatycznie.|

## <a name="settings-blend-only"></a>Ustawienia (tylko program Blend)

Użyj tych opcji, aby określić ustawienia podczas edytowania plików XAML w programie Blend.

|||
|-|-|
|**Powiększ za pomocą**|Powiększenie w Projektancie XAML przy użyciu kółka myszy lub naciskając **Ctrl** lub **Alt** klucza przy użyciu kółka myszy.|
|**Typ jednostki**|Określa, czy pomiary w Projektancie są oparte na punktach lub pikselach. Ponieważ Universal Windows Apps nie obsługują punkty, jednostki są automatycznie konwertowane na pikseli, jeśli **punktów** jest zaznaczone.|

## <a name="artboard-blend-only"></a>Obszar roboczy (tylko program Blend)

Użyj tych ustawień, aby określić zachowanie projektanta XAML podczas edycji dokumentów XAML w programie Blend.

### <a name="snapping"></a>Przyciągania

|||
|-|-|
|**Pokaż siatkę przyciągania**|Gdy ta opcja jest zaznaczona, linie siatki są wyświetlane w Projektancie ułatwiające wyrównywanie formantów. Formanty dodane do projektanta przyciągania do siatki te podczas **przyciąganie do linii siatki** opcja jest zaznaczona.|
|**Przyciąganie do linii siatki**|Po dodaniu kontrolki lub przenosić w granicach projektanta, są one przyciągane do siatki.|
|**Odstępy siatki**|Określa odstępy między liniami siatki w pikselach lub punkty (zgodnie z ustaleniami **typ jednostki** ustawienie).|
|**Przyciąganie do linii wyrównania**|Określa, czy formanty mają być przyciągane do linii wyrównania.|
|**Margines domyślny**|Gdy **przyciąganie do linii wyrównania** jest włączone, określa odstępy między liniami przyciągania i kontrolki w pikselach lub punkty (zgodnie z ustaleniami **typ jednostki** ustawienie).|
|**Domyślnie, wypełnienie**|Gdy **przyciąganie do linii wyrównania** jest włączone, określa dodatkowy odstęp między formantem i linii przyciągania w pikselach lub punkty (zgodnie z ustaleniami **typ jednostki** ustawienie).|

### <a name="animation"></a>Animacja

Użyj tego ustawienia, aby określić, czy zostanie wyświetlone ostrzeżenie podczas zależne (bez akceleracji) w programie Blend włączone są animacje.

### <a name="effects"></a>Efekty

Użyj tych ustawień, aby określić, czy efekty mają być renderowane podczas edycji XAML plików w Projektancie XAML przy użyciu programu Blend.

|||
|-|-|
|**Renderowanie efektów**|Określa, czy efekty renderowania podczas edycji plików XAML w Projektancie XAML przy użyciu programu Blend.|
|**Próg powiększenia**|Określa procent powiększenia, w których efekty renderowania, kiedy **Renderowanie efektów** pole wyboru jest zaznaczone. Przy powiększeniu poza to ustawienie, efekty już renderowania w Projektancie XAML.|

## <a name="see-also"></a>Zobacz także

- [XAML w WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Przewodnik: Mój pierwszy aplikacji klasycznej WPF](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)