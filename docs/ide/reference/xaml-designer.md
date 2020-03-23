---
title: Strona opcji Projektanta XAML
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585616"
---
# <a name="xaml-designer-options-page"></a>Strona opcji Projektanta XAML

Strona Opcje **Projektanta XAML** służy do określania sposobu formatowania elementów i atrybutów w dokumentach XAML. Aby otworzyć tę stronę, wybierz menu **Narzędzia,** a następnie wybierz polecenie **Opcje**. Aby uzyskać dostęp do strony właściwości **projektanta XAML,** wybierz węzeł **ProjektantA XAML.** Ustawienia projektanta XAML są stosowane po otwarciu dokumentu. Tak, jeśli wniesiesz zmiany do ustawień, należy zamknąć, a następnie ponownie otworzyć program Visual Studio, aby zobaczyć zmiany.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz polecenie **Importuj i eksportuj ustawienia** w menu **Narzędzia.** Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../environment-settings.md#reset-settings).

## <a name="enable-xaml-designer"></a>Włączanie projektanta XAML

Po wybraniu tej opcji to ustawienie włącza projektanta XAML. Projektant XAML udostępnia wizualny obszar roboczy do edytowania dokumentów XAML. Niektóre funkcje w programie Visual Studio, takie jak IntelliSense dla zasobów i powiązania danych, wymagają włączenia projektanta XAML.

Poniższe ustawienia mają zastosowanie tylko wtedy, gdy włączony jest projektant XAML. Jeśli ta opcja zostanie zmieniona, należy ponownie uruchomić program Visual Studio, aby to ustawienie zostało zastosowane.

## <a name="default-document-view"></a>Domyślny widok dokumentu

To ustawienie służy do określania, czy widok projektowy jest wyświetlany podczas ładowania dokumentów XAML.

|||
|-|-|
|**Widok źródłowy**|Określa, czy w widoku XAML jest wyświetlane tylko źródło XAML. Jest to przydatne podczas ładowania dużych dokumentów.|
|**Widok projektu**|Określa, czy w widoku XAML jest wyświetlany tylko wizualny projektant XAML.|
|**Widok dzielony**|Określa, czy zarówno wizualny projektant XAML, jak i źródło XAML są wyświetlane obok siebie w widoku XAML (lokalizacja oparta na ustawieniu **Orientacja podziału).**|

## <a name="split-orientation"></a>Orientacja podziału

To ustawienie służy do kontrolowania, kiedy i jak projektant XAML pojawia się podczas edytowania dokumentu XAML. Te ustawienia mają zastosowanie tylko wtedy, gdy **domyślny widok dokumentu** jest ustawiony na **Widok podzielony**.

|||
|-|-|
|**Pionowa**|Źródło XAML pojawia się po lewej stronie widoku XAML, a projektant XAML pojawia się po drugiej stronie.|
|**Poziome**|Projektant XAML pojawia się w górnej części widoku XAML, a źródło XAML pojawi się pod nim.|
|**Domyślny**|Dokument XAML używa orientacji podziału zalecane dla platformy, do której odnosi się projekt dokumentu. W przypadku większości platform jest to **równoważne poziomemu**.|

## <a name="zoom-by-using"></a>Powiększanie za pomocą

To ustawienie służy do określania działania powiększania podczas edytowania dokumentu XAML.

|||
|-|-|
|**Kółka myszy**|Powiększ projektanta XAML, przewijając kółko myszy.|
|**Ctrl + kółko myszy**|Powiększ projektanta XAML, naciskając klawisz **Ctrl** podczas przewijania kółka myszy.|
|**Alt + kółko myszy**|Powiększ projektanta XAML, naciskając klawisz **Alt** podczas przewijania kółka myszy.|

Te ustawienia określają zachowanie projektanta podczas edytowania dokumentu XAML.

|||
|-|-|
|**Automatyczne nazywanie elementów interaktywnych podczas tworzenia**|Określa, czy nazwa domyślna jest podana dla nowego elementu interaktywnego po dodaniu go do projektanta.|
|**Automatyczne wstawianie właściwości układu podczas tworzenia elementu**|Określa, czy właściwości układu są dostarczane dla nowego elementu po dodaniu go do projektanta. Właściwości układu to te, które mają wpływ na układ formantu, na przykład Margin i VerticalAlignment. Poniższy kod XAML pokazuje, jak tworzony jest przycisk z i bez tej wybranej opcji:<br />`<Button Content="Button" HorizontalAlignment="Left" Margin="245,56,0,0" Grid.Row="1" VerticalAlignment="Top" Width="75"/>`<br />`<Button Content="Button" Grid.Row="1"/>`|
|**Korzystanie z układu opartego na kwadrancie**|Określa, czy aktualnie zaznaczony formant jest wyrównany do najbliższych krawędzi kontenera nadrzędnego. Jeśli to pole wyboru jest wyczyszczone, wyrównanie formantu nie zmienia się podczas przenoszenia ani tworzenia operacji.|
|**Automatyczne wypełnianie elementów przybornika**|Określa, czy formanty użytkownika i formanty niestandardowe w bieżącym rozwiązaniu są automatycznie wyświetlane w przyborniku.|

## <a name="settings-blend-only"></a>Ustawienia (tylko mieszanie)

Te opcje służą do określania ustawień podczas edytowania plików XAML przy użyciu programu Blend.

|||
|-|-|
|**Powiększanie za pomocą**|Powiększanie projektanta XAML przez przewijanie kółka myszy lub naciśnięcie klawisza **Ctrl** lub **Alt** podczas przewijania kółka myszy.|
|**Jednostki typu**|Określa, czy pomiary na projektancie są oparte na punktach czy pikselach. Ponieważ uniwersalne aplikacje systemu Windows nie obsługują punktów, jednostki są automatycznie konwertowane na piksele, jeśli **wybrano opcję Punkty.**|

## <a name="artboard-blend-only"></a>Obszar roboczy (tylko mieszanie)

Te ustawienia służą do określania zachowania projektanta XAML podczas edytowania dokumentów XAML w aplikacji Blend.

### <a name="snapping"></a>Przyciąganie

|||
|-|-|
|**Pokaż siatkę przyciągania**|Gdy ta opcja jest zaznaczona, linie siatki są wyświetlane w projektancie, aby ułatwić wyrównywanie formantów. Formanty dodane do przyciągania projektanta do tych linii siatki po wybraniu opcji **Przystaw do linii siatki.**|
|**Przyciąganie do linii siatki**|Gdy formanty są dodawane lub przenoszone wokół projektanta, są przyciągane do linii siatki.|
|**Odstępy między liniami siatki**|Określa odstępy między liniami siatki w pikselach lub punktach (określone przez ustawienie **Jednostki typu).**|
|**Przyciąganie do linii przyciągania**|Określa, czy formanty są przyciągane do linii przyciągania.|
|**Margines domyślny**|Gdy **opcja Przyciągaj do snaplinów** jest włączona, określa odstępy między formantem a liniami przyciągania w pikselach lub punktach (zgodnie z **ustawieniem Jednostki typu).**|
|**Domyślna dopełnienie**|Gdy **opcja Przyciągaj do snaplinów** jest włączona, określa dodatkowe odstępy między formantem a liniami przyciągania w pikselach lub punktach (zgodnie z **ustawieniem Jednostki typu).**|

### <a name="animation"></a>Animacja

To ustawienie służy do określania, czy ostrzeżenie jest wyświetlane, gdy animacje zależne (nieprzyśpiegowane) są włączone w trybie Blend.

### <a name="effects"></a>Efekty

Użyj tych ustawień, aby określić, czy efekty są renderowane podczas edytowania plików XAML w Projektancie XAML przy użyciu programu Blend.

|||
|-|-|
|**Renderowanie efektów**|Określa, czy efekty są renderowane podczas edytowania plików XAML w Projektancie XAML przy użyciu programu Blend.|
|**Próg powiększenia**|Określa procent powiększenia, który efekt jest renderowany po zaznaczeniu pola wyboru **Renderowanie efektów.** Jeśli powiększysz poza to ustawienie, efekty nie będą już renderowane w Projektancie XAML.|

## <a name="see-also"></a>Zobacz też

- [XAML w WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Instruktaż: Moja pierwsza aplikacja komputerowa WPF](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)
